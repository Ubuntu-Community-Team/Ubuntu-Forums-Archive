---
title: "Wireless constantly disconnecting and reconnecting"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by jllb on 2010-08-02
The wireless is constantly disconnecting and reconnecting. Nevertheless, it possible to use the internet using the wireless connection, with some trouble. Any help will be very appreciated. 

A (partial) output of the daemon.log is 
```
Aug  2 08:49:37 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:49:37 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:49:37 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:49:40 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:49:40 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:49:40 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:49:40 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:49:40 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:49:40 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:49:40 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:49:40 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:49:40 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:50:28 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:50:28 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:50:28 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:50:31 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:50:31 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:50:31 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:50:31 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:50:31 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:50:31 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:50:31 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:50:31 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:50:31 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:50:57 antonio-laptop ddclient[1163]: WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''
Aug  2 08:50:58 antonio-laptop ddclient[1163]: FAILED:   updating Home: nohost: The hostname specified does not exist in the database
Aug  2 08:51:36 antonio-laptop ntpd[2766]: synchronized to 134.214.100.6, stratum 2
Aug  2 08:51:36 antonio-laptop ntpd[2766]: kernel time sync status change 2001
Aug  2 08:51:38 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:51:38 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:51:38 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:51:41 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:51:41 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:51:41 antonio-laptop wpa_supplicant[882]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Aug  2 08:51:41 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:51:41 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:51:42 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:51:42 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:51:42 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:51:42 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:51:42 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:51:57 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:51:57 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:51:57 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:52:00 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:52:00 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:52:00 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:52:00 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:52:00 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:52:00 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:52:00 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:52:00 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:52:00 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:52:33 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:52:33 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:52:33 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:52:36 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:52:36 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:52:38 antonio-laptop NetworkManager: <debug> [1280731958.002105] periodic_update(): Roamed from BSSID 00:23:48:74:F2:34 (Orange_F233) to (none) ((none))
Aug  2 08:52:46 antonio-laptop wpa_supplicant[882]: Authentication with 00:23:48:74:f2:34 timed out.
Aug  2 08:52:46 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Aug  2 08:52:46 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Aug  2 08:52:49 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2629
Aug  2 08:52:49 antonio-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Aug  2 08:52:49 antonio-laptop avahi-daemon[792]: Withdrawing address record for 192.168.0.10 on wlan0.
Aug  2 08:52:49 antonio-laptop avahi-daemon[792]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.10.
Aug  2 08:52:49 antonio-laptop avahi-daemon[792]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Orange_F233'
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Orange_F233' has security, and secrets exist.  No new secrets needed.
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Config: added 'ssid' value 'Orange_F233'
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug  2 08:52:49 antonio-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  2 08:52:49 antonio-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug  2 08:52:49 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:52:52 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:52:52 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:52:52 antonio-laptop wpa_supplicant[882]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Aug  2 08:52:52 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:52:52 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:52:53 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:52:53 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Orange_F233'.
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  dhclient started with pid 2842
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug  2 08:52:53 antonio-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug  2 08:52:53 antonio-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug  2 08:52:53 antonio-laptop dhclient: All rights reserved.
Aug  2 08:52:53 antonio-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug  2 08:52:53 antonio-laptop dhclient: 
Aug  2 08:52:53 antonio-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug  2 08:52:53 antonio-laptop dhclient: Listening on LPF/wlan0/00:1f:3c:36:2a:32
Aug  2 08:52:53 antonio-laptop dhclient: Sending on   LPF/wlan0/00:1f:3c:36:2a:32
Aug  2 08:52:53 antonio-laptop dhclient: Sending on   Socket/fallback
Aug  2 08:52:57 antonio-laptop dhclient: DHCPREQUEST of 192.168.0.10 on wlan0 to 255.255.255.255 port 67
Aug  2 08:52:57 antonio-laptop dhclient: DHCPACK of 192.168.0.10 from 192.168.0.1
Aug  2 08:52:57 antonio-laptop dhclient: bound to 192.168.0.10 -- renewal in 41828 seconds.
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>    address 192.168.0.10
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>    gateway 192.168.0.1
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>    domain name 'home'
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  2 08:52:57 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  2 08:52:57 antonio-laptop avahi-daemon[792]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.10.
Aug  2 08:52:57 antonio-laptop avahi-daemon[792]: New relevant interface wlan0.IPv4 for mDNS.
Aug  2 08:52:57 antonio-laptop avahi-daemon[792]: Registering new address record for 192.168.0.10 on wlan0.IPv4.
Aug  2 08:52:58 antonio-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug  2 08:52:58 antonio-laptop NetworkManager: <info>  Policy set 'Auto Orange_F233' (wlan0) as default for routing and DNS.
Aug  2 08:52:58 antonio-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug  2 08:52:58 antonio-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  2 08:52:58 antonio-laptop ntpd[2766]: ntpd exiting on signal 15
Aug  2 08:52:59 antonio-laptop ntpdate[2931]: adjust time server 134.214.100.6 offset 0.075786 sec
Aug  2 08:52:59 antonio-laptop ntpd[2975]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 00:28:40 UTC 2010 (1)
Aug  2 08:52:59 antonio-laptop ntpd[2976]: precision = 2.000 usec
Aug  2 08:52:59 antonio-laptop ntpd[2976]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug  2 08:52:59 antonio-laptop ntpd[2976]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug  2 08:52:59 antonio-laptop ntpd[2976]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Aug  2 08:52:59 antonio-laptop ntpd[2976]: Listening on interface #2 wlan0, 192.168.0.10#123 Enabled
Aug  2 08:52:59 antonio-laptop ntpd[2976]: kernel time sync status 2040
Aug  2 08:52:59 antonio-laptop ntpd[2976]: frequency initialized 12.705 PPM from /var/lib/ntp/ntp.drift
Aug  2 08:52:59 antonio-laptop ntpd[2976]: getaddrinfo: "::1" invalid host address, ignored
Aug  2 08:53:17 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:53:17 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:53:17 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:53:19 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:53:19 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:53:19 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:53:19 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:53:19 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:53:19 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:53:19 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:53:19 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:53:19 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  2 08:53:57 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  2 08:53:57 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  2 08:53:57 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  2 08:53:59 antonio-laptop wpa_supplicant[882]: Trying to associate with 00:23:48:74:f2:34 (SSID='Orange_F233' freq=2412 MHz)
Aug  2 08:53:59 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  2 08:53:59 antonio-laptop wpa_supplicant[882]: Associated with 00:23:48:74:f2:34
Aug  2 08:53:59 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  2 08:53:59 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  2 08:53:59 antonio-laptop wpa_supplicant[882]: WPA: Key negotiation completed with 00:23:48:74:f2:34 [PTK=CCMP GTK=TKIP]
Aug  2 08:53:59 antonio-laptop wpa_supplicant[882]: CTRL-EVENT-CONNECTED - Connection to 00:23:48:74:f2:34 completed (reauth) [id=0 id_str=]
Aug  2 08:53:59 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 08:53:59 antonio-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
```

Other information:

1. Machine brand and model: Toshiba Satellite A300

2. Wireless Brand, Model and Wireless Chipset:
```
antonio@antonio-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
antonio@antonio-laptop:~$ 

```
```
antonio@antonio-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
antonio@antonio-laptop:~$ 

```

3. Check interface:
```
antonio@antonio-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:45:ad:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19536 (19.5 KB)  TX bytes:19536 (19.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:36:2a:32  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4469553 (4.4 MB)  TX bytes:1099668 (1.0 MB)

```
```
antonio@antonio-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Orange_F233"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:48:74:F2:34   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

4. Check for modules:
```
antonio@antonio-laptop:~$ lsmod
Module                  Size  Used by
btrfs                 458938  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8933  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172682  0 
xfs                   515548  0 
exportfs                3437  1 xfs
reiserfs              225539  0 
webcamstudio           12383  0 
binfmt_misc             6587  1 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
ppdev                   5259  0 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168721  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22641  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_hda_intel          21941  2 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
vga16fb                11385  0 
snd_hwdep               5412  1 snd_hda_codec
vgastate                8961  1 vga16fb
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  285076  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
iwl3945                68727  0 
joydev                  8708  0 
drm_kms_helper         29297  1 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               105922  1 iwl3945
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
sdhci_pci               5470  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205146  2 iwl3945,iwlcore
sdhci                  15462  1 sdhci_pci
uvcvideo               56990  0 
video                  17375  1 i915
soundcore               6620  1 snd
psmouse                63245  0 
intel_agp              24119  2 i915
cfg80211              126517  3 iwl3945,iwlcore,mac80211
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  3 iwl3945,iwlcore,sdhci
serio_raw               3978  0 
lp                      7028  0 
agpgart                31724  2 drm,intel_agp
videodev               34361  2 webcamstudio,uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
sky2                   40775  0 
ahci                   32200  2 

```

5. Kernel boot messages: 
```
[ 1465.098748] wlan0: direct probe responded
[ 1465.098757] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1465.100569] wlan0: authenticated
[ 1465.100606] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1465.102984] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1465.102992] wlan0: associated
[ 1498.500253] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1501.346903] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1501.349934] wlan0: direct probe responded
[ 1501.349943] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1501.351791] wlan0: authenticated
[ 1501.351826] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1501.354302] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1501.354310] wlan0: associated
[ 1563.500088] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1566.321040] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1566.323379] wlan0: direct probe responded
[ 1566.323388] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1566.325190] wlan0: authenticated
[ 1566.325229] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1566.327537] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1566.327544] wlan0: associated
[ 1582.160299] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1584.971950] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1584.974918] wlan0: direct probe responded
[ 1584.974927] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1584.976803] wlan0: authenticated
[ 1584.976840] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1584.979249] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1584.979256] wlan0: associated
[ 1702.156272] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1705.003068] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1705.200238] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 1705.202586] wlan0: direct probe responded
[ 1705.202592] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1705.204411] wlan0: authenticated
[ 1705.204454] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1705.206919] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1705.206925] wlan0: associated
[ 1738.500279] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1741.341741] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1741.540308] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 1741.544795] wlan0: direct probe responded
[ 1741.544802] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1741.546608] wlan0: authenticated
[ 1741.546647] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1741.549024] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1741.549031] wlan0: associated
[ 1793.500075] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1796.271300] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1796.468344] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 1796.470682] wlan0: direct probe responded
[ 1796.470688] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1796.472540] wlan0: authenticated
[ 1796.472584] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1796.474927] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1796.474933] wlan0: associated
[ 1822.157285] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1825.026725] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1825.029165] wlan0: direct probe responded
[ 1825.029174] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1825.031049] wlan0: authenticated
[ 1825.031087] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1825.033412] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1825.033419] wlan0: associated
[ 1917.488317] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1920.349654] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1920.548313] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 1920.748250] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 1920.948074] wlan0: direct probe to AP 00:23:48:74:f2:34 timed out
[ 1933.037620] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1933.237048] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 1933.436243] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 1933.438582] wlan0: direct probe responded
[ 1933.438588] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1933.440515] wlan0: authenticated
[ 1933.440561] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1933.442994] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1933.443000] wlan0: associated
[ 1936.488309] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 1946.654484] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 1946.657007] wlan0: direct probe responded
[ 1946.657015] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 1946.658818] wlan0: authenticated
[ 1946.658856] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 1946.662083] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 1946.662091] wlan0: associated
[ 2002.500308] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2005.342355] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2005.345048] wlan0: direct probe responded
[ 2005.345056] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2005.346950] wlan0: authenticated
[ 2005.346990] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2005.349311] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2005.349314] wlan0: associated
[ 2062.148277] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2064.998007] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2065.000957] wlan0: direct probe responded
[ 2065.000963] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2065.002749] wlan0: authenticated
[ 2065.002770] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2065.006968] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2065.006973] wlan0: associated
[ 2102.084270] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2104.929240] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2105.129061] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2105.131465] wlan0: direct probe responded
[ 2105.131473] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2105.133581] wlan0: authenticated
[ 2105.133620] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2105.136056] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2105.136063] wlan0: associated
[ 2162.092080] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2164.901797] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2165.100306] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2165.102724] wlan0: direct probe responded
[ 2165.102730] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2165.104659] wlan0: authenticated
[ 2165.104700] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2165.107101] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2165.107106] wlan0: associated
[ 2242.068276] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2244.872422] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2244.874765] wlan0: direct probe responded
[ 2244.874773] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2244.876589] wlan0: authenticated
[ 2244.876629] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2244.879007] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2244.879015] wlan0: associated
[ 2331.488261] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2334.259625] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2334.261960] wlan0: direct probe responded
[ 2334.261968] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2334.263765] wlan0: authenticated
[ 2334.263802] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2334.266169] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2334.266176] wlan0: associated
[ 2396.488263] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2399.270514] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2399.272849] wlan0: direct probe responded
[ 2399.272857] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2399.274674] wlan0: authenticated
[ 2399.274710] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2399.277146] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2399.277153] wlan0: associated
[ 2461.932286] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2464.716376] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2464.719341] wlan0: direct probe responded
[ 2464.719350] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2464.721526] wlan0: authenticated
[ 2464.721566] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2464.723904] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2464.723912] wlan0: associated
[ 2513.488262] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2516.285901] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2516.484080] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2516.486509] wlan0: direct probe responded
[ 2516.486517] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2516.488419] wlan0: authenticated
[ 2516.488460] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2516.490817] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2516.490822] wlan0: associated
[ 2582.156268] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2584.938666] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2584.941130] wlan0: direct probe responded
[ 2584.941138] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2584.942955] wlan0: authenticated
[ 2584.942993] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2584.945430] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2584.945438] wlan0: associated
[ 2630.488054] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2633.327012] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2633.330112] wlan0: direct probe responded
[ 2633.330121] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2633.331928] wlan0: authenticated
[ 2633.331968] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2633.334318] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2633.334326] wlan0: associated
[ 2702.072082] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2704.909349] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2705.108099] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2705.308292] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 2705.508297] wlan0: direct probe to AP 00:23:48:74:f2:34 timed out
[ 2717.572404] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2717.772289] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2717.774642] wlan0: direct probe responded
[ 2717.774648] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2717.776533] wlan0: authenticated
[ 2717.776571] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2717.778903] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2717.778909] wlan0: associated
[ 2766.488251] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2769.298050] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2769.300419] wlan0: direct probe responded
[ 2769.300427] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2769.302259] wlan0: authenticated
[ 2769.302298] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2769.304638] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2769.304646] wlan0: associated
[ 2822.084285] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2824.873951] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2825.072080] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2825.273261] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 2825.275598] wlan0: direct probe responded
[ 2825.275602] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2825.277536] wlan0: authenticated
[ 2825.277565] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2825.279880] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2825.279884] wlan0: associated
[ 2861.920271] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2864.675246] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2864.678275] wlan0: direct probe responded
[ 2864.678283] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2864.680185] wlan0: authenticated
[ 2864.680222] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2864.682664] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2864.682671] wlan0: associated
[ 2922.132069] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2924.933658] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2925.132289] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2925.134633] wlan0: direct probe responded
[ 2925.134640] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2925.136536] wlan0: authenticated
[ 2925.136578] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2925.139024] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2925.139031] wlan0: associated
[ 2958.500078] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 2961.358246] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 2961.557285] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 2961.559637] wlan0: direct probe responded
[ 2961.559643] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 2961.561526] wlan0: authenticated
[ 2961.561565] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 2961.563987] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 2961.563993] wlan0: associated
[ 3001.904096] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3004.675924] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3004.872306] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 3005.072090] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 3005.074459] wlan0: direct probe responded
[ 3005.074465] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3005.076277] wlan0: authenticated
[ 3005.076314] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3005.078731] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3005.078737] wlan0: associated
[ 3078.500244] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3081.290922] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3081.293356] wlan0: direct probe responded
[ 3081.293364] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3081.295163] wlan0: authenticated
[ 3081.295199] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3081.297626] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3081.297633] wlan0: associated
[ 3102.152264] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3104.984991] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3104.988985] wlan0: direct probe responded
[ 3104.988993] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3104.990804] wlan0: authenticated
[ 3104.990842] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3104.993330] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3104.993337] wlan0: associated
[ 3142.500087] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3145.282152] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3145.284917] wlan0: direct probe responded
[ 3145.284925] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3145.286788] wlan0: authenticated
[ 3145.286823] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3145.289133] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3145.289141] wlan0: associated
[ 3222.064279] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3224.900492] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3224.902816] wlan0: direct probe responded
[ 3224.902824] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3224.904665] wlan0: authenticated
[ 3224.904702] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3224.907108] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3224.907115] wlan0: associated
[ 3293.488259] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3296.267047] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3296.274265] wlan0: direct probe responded
[ 3296.274274] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3296.276713] wlan0: authenticated
[ 3296.276754] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3296.279182] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3296.279189] wlan0: associated
[ 3342.076295] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3344.897762] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3344.900615] wlan0: direct probe responded
[ 3344.900623] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3344.902546] wlan0: authenticated
[ 3344.902583] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3344.904951] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3344.904954] wlan0: associated
[ 3413.488283] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3416.305608] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3416.504307] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 3416.704269] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 3416.707444] wlan0: direct probe responded
[ 3416.707450] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3416.709255] wlan0: authenticated
[ 3416.709294] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3416.711728] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3416.711734] wlan0: associated
[ 3461.888072] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3464.724816] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3464.727147] wlan0: direct probe responded
[ 3464.727155] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3464.729128] wlan0: authenticated
[ 3464.729166] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3464.731486] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3464.731493] wlan0: associated
[ 3533.500296] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3536.313689] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3536.316138] wlan0: direct probe responded
[ 3536.316146] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3536.317948] wlan0: authenticated
[ 3536.317985] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3536.320338] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3536.320345] wlan0: associated
[ 3582.104292] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3584.871233] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3584.873927] wlan0: direct probe responded
[ 3584.873935] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3584.875737] wlan0: authenticated
[ 3584.875772] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3584.878619] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3584.878627] wlan0: associated
[ 3618.488345] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3621.305105] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3621.504292] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 3621.704242] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 3)
[ 3621.904066] wlan0: direct probe to AP 00:23:48:74:f2:34 timed out
[ 3633.994109] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3633.996450] wlan0: direct probe responded
[ 3633.996457] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3633.998358] wlan0: authenticated
[ 3633.998390] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3634.000763] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3634.000769] wlan0: associated
[ 3634.121079] wlan0: deauthenticating from 00:23:48:74:f2:34 by local choice (reason=3)
[ 3634.168872] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3634.168892] wlan0: deauthenticating from 00:23:48:74:f2:34 by local choice (reason=3)
[ 3634.168920] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3634.171939] wlan0: direct probe responded
[ 3634.171944] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3634.176497] wlan0: authenticated
[ 3634.176519] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3634.179743] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3634.179747] wlan0: associated
[ 3701.904116] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3704.712437] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3704.912689] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 3704.915064] wlan0: direct probe responded
[ 3704.915072] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3704.916876] wlan0: authenticated
[ 3704.916920] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3704.919357] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3704.919362] wlan0: associated
[ 3742.148304] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3744.956183] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3744.959319] wlan0: direct probe responded
[ 3744.959328] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3744.961148] wlan0: authenticated
[ 3744.961183] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3744.963571] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3744.963579] wlan0: associated
[ 3801.952305] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3804.780762] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3804.788098] wlan0: direct probe responded
[ 3804.788107] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3804.790018] wlan0: authenticated
[ 3804.790057] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3804.792514] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3804.792521] wlan0: associated
[ 3882.132092] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3884.944067] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3884.946396] wlan0: direct probe responded
[ 3884.946404] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3884.948268] wlan0: authenticated
[ 3884.948308] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3884.951184] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3884.951192] wlan0: associated
[ 3981.872277] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 3984.776279] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 3984.779266] wlan0: direct probe responded
[ 3984.779274] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 3984.781122] wlan0: authenticated
[ 3984.781158] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 3984.783499] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 3984.783506] wlan0: associated
[ 4073.488297] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 4076.255040] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 4076.257380] wlan0: direct probe responded
[ 4076.257388] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 4076.259235] wlan0: authenticated
[ 4076.259272] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 4076.261883] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 4076.261891] wlan0: associated
[ 4102.092308] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 4104.821001] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 4105.020304] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 2)
[ 4105.022677] wlan0: direct probe responded
[ 4105.022684] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 4105.024539] wlan0: authenticated
[ 4105.024601] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 4105.027089] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 4105.027095] wlan0: associated
[ 4139.488241] No probe response from AP 00:23:48:74:f2:34 after 500ms, disconnecting.
[ 4142.307191] wlan0: direct probe to AP 00:23:48:74:f2:34 (try 1)
[ 4142.309845] wlan0: direct probe responded
[ 4142.309853] wlan0: authenticate with AP 00:23:48:74:f2:34 (try 1)
[ 4142.311722] wlan0: authenticated
[ 4142.311758] wlan0: associate with AP 00:23:48:74:f2:34 (try 1)
[ 4142.314179] wlan0: RX AssocResp from 00:23:48:74:f2:34 (capab=0x411 status=0 aid=1)
[ 4142.314187] wlan0: associated

```

6. Network configuration:
```
antonio@antonio-laptop:~$ sudo lshw -C network
[sudo] password for antonio: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:36:2a:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.10 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:f0300000-f0300fff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:45:ad:c1
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0200000-f0203fff ioport:2000(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```
7. Scan for networks:
```
antonio@antonio-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:48:74:F2:34
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Orange_F233"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000024a760df5
                    Extra: Last beacon: 33844ms ago
                    IE: Unknown: 000B4F72616E67655F46323333
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000

vboxnet0  Interface doesn't support scanning.

```

8. Ubuntu version:
```
antonio@antonio-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS

```

9. Kernel/architecture:
```
antonio@antonio-laptop:~$ uname -mr
2.6.32-24-generic i686

```

10. Restarting the network:
```
antonio@antonio-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

---

### Post by jllb on 2010-08-03
Toc, toc.
Anyone any idea, please?

---

### Post by jllb on 2010-08-03
Installing wicd and removing network manager seems to have solved the issue.

---

### Post by geri1590 on 2010-12-21
Hi, I had the same problem more or less. I have a similar hardware to *TP-LINK WN821N,*and with ar9170usb module and network-manager, the connection was unstable. It was disconnected every half an hour or less. The log said: 
```
geri1590-desktop kernel: [ 2629.110033] No probe response from AP <AP> after 500ms, disconnecting.
geri1590-desktop kernel: [ 2631.575838] ADDRCONF(NETDEV_UP): wlan1: link is not ready
```I uninstalled network-manager, then I installed wicd and now it doesn't disconnect, it works perfectly.

Thank you for posting the solution :D.

---

### Post by geri1590 on 2010-12-26
Ok, I didn't say nothing. The problem still there. Every 10-20min (depending in the internet use) the network disconnects.

---

### Post by silvari on 2011-12-31
FWIW... I struggled quite a bit with this issue on my Toshiba NB205 (running Maverick), and tried many suggestions, including:

-- installing linux-backports-modules-compat-wireless-2.6.36-maverick-generic, as per: [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

-- adding 'nohwcrypt=1' to /etc/modprobe.d/ath9k.conf

... but without success. 

Eventually I removed the Atheros AR9285 wireless card from the laptop, and replaced it with the Broadcom card taken from an HP Mini 1030NR . Happiness followed.

---

