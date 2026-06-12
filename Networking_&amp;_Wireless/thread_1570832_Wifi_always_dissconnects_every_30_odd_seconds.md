---
title: "Wifi always dissconnects every 30 odd seconds"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by Alex E on 2010-09-08
Hi all im fairly familiar with Ubuntu and the workings but im having issues with my wireless network disconnecting every 30 seconds and taking another 20 to reconnect i could use a hand. i managed to pull some stuff outa the log files hope it helps. o also when i get disconnected everyone else on the wireless router gets disconnected but if i booted into windows its fine.

Im using Ubuntu 10.4 on a acer aspire 6930g

Sep  8 23:28:58 alex-laptop kernel: [ 4675.621431] iwlagn 0000:07:00.0: RF_KILL bit toggled to enable radio.
Sep  8 23:28:59 alex-laptop NetworkManager: <info>  (wlan0): bringing up device.
Sep  8 23:28:59 alex-laptop kernel: [ 4676.665693] Registered led device: iwl-phy0::radio
Sep  8 23:28:59 alex-laptop kernel: [ 4676.665742] Registered led device: iwl-phy0::assoc
Sep  8 23:28:59 alex-laptop kernel: [ 4676.665786] Registered led device: iwl-phy0::RX
Sep  8 23:28:59 alex-laptop kernel: [ 4676.665830] Registered led device: iwl-phy0::TX
Sep  8 23:28:59 alex-laptop kernel: [ 4676.676499] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  8 23:28:59 alex-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Sep  8 23:28:59 alex-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto WiFi'
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto WiFi' has security, and secrets exist.  No new secrets needed.
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Config: added 'ssid' value 'WiFi'
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep  8 23:29:02 alex-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  8 23:29:02 alex-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Sep  8 23:29:02 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Sep  8 23:29:07 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep  8 23:29:10 alex-laptop wpa_supplicant[900]: Trying to associate with 00:02:6f:54:75:2f (SSID='WiFi' freq=2447 MHz)
Sep  8 23:29:10 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep  8 23:29:10 alex-laptop kernel: [ 4688.008645] wlan0: deauthenticating from 00:02:6f:54:75:2f by local choice (reason=3)
Sep  8 23:29:10 alex-laptop kernel: [ 4688.008815] wlan0: direct probe to AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:10 alex-laptop kernel: [ 4688.012195] wlan0: direct probe responded
Sep  8 23:29:10 alex-laptop kernel: [ 4688.012205] wlan0: authenticate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:10 alex-laptop kernel: [ 4688.013978] wlan0: authenticated
Sep  8 23:29:10 alex-laptop kernel: [ 4688.014019] wlan0: associate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:11 alex-laptop kernel: [ 4688.023650] wlan0: RX AssocResp from 00:02:6f:54:75:2f (capab=0x411 status=0 aid=1)
Sep  8 23:29:11 alex-laptop kernel: [ 4688.023658] wlan0: associated
Sep  8 23:29:11 alex-laptop kernel: [ 4688.035697] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep  8 23:29:11 alex-laptop wpa_supplicant[900]: Associated with 00:02:6f:54:75:2f
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Sep  8 23:29:11 alex-laptop wpa_supplicant[900]: WPA: Key negotiation completed with 00:02:6f:54:75:2f [PTK=TKIP GTK=TKIP]
Sep  8 23:29:11 alex-laptop wpa_supplicant[900]: CTRL-EVENT-CONNECTED - Connection to 00:02:6f:54:75:2f completed (auth) [id=0 id_str=]
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'WiFi'.
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  dhclient started with pid 4106
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep  8 23:29:11 alex-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Sep  8 23:29:11 alex-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Sep  8 23:29:11 alex-laptop dhclient: All rights reserved.
Sep  8 23:29:11 alex-laptop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Sep  8 23:29:11 alex-laptop dhclient: 
Sep  8 23:29:11 alex-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Sep  8 23:29:11 alex-laptop dhclient: Listening on LPF/wlan0/00:21:5d:42:e5:08
Sep  8 23:29:11 alex-laptop dhclient: Sending on   LPF/wlan0/00:21:5d:42:e5:08
Sep  8 23:29:11 alex-laptop dhclient: Sending on   Socket/fallback
Sep  8 23:29:12 alex-laptop dhclient: DHCPREQUEST of 192.168.1.69 on wlan0 to 255.255.255.255 port 67
Sep  8 23:29:12 alex-laptop dhclient: DHCPACK of 192.168.1.69 from 192.168.1.254
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  8 23:29:12 alex-laptop NetworkManager: <info>    address 192.168.1.69
Sep  8 23:29:12 alex-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep  8 23:29:12 alex-laptop NetworkManager: <info>    gateway 192.168.1.254
Sep  8 23:29:12 alex-laptop NetworkManager: <info>    nameserver '192.168.1.254'
Sep  8 23:29:12 alex-laptop NetworkManager: <info>    domain name 'home'
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  8 23:29:12 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep  8 23:29:12 alex-laptop avahi-daemon[898]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.69.
Sep  8 23:29:12 alex-laptop avahi-daemon[898]: New relevant interface wlan0.IPv4 for mDNS.
Sep  8 23:29:12 alex-laptop avahi-daemon[898]: Registering new address record for 192.168.1.69 on wlan0.IPv4.
Sep  8 23:29:12 alex-laptop dhclient: bound to 192.168.1.69 -- renewal in 35121 seconds.
Sep  8 23:29:12 alex-laptop avahi-daemon[898]: Registering new address record for fe80::221:5dff:fe42:e508 on wlan0.*.
Sep  8 23:29:13 alex-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Sep  8 23:29:13 alex-laptop NetworkManager: <info>  Policy set 'Auto WiFi' (wlan0) as default for routing and DNS.
Sep  8 23:29:13 alex-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Sep  8 23:29:13 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  8 23:29:14 alex-laptop ntpdate[4149]: adjust time server 91.189.94.4 offset -0.000184 sec
Sep  8 23:29:21 alex-laptop kernel: [ 4698.324253] wlan0: no IPv6 routers present
Sep  8 23:29:25 alex-laptop kernel: [ 4702.903201] wlan0: disassociated from 00:02:6f:54:75:2f (Reason: 14)
Sep  8 23:29:25 alex-laptop kernel: [ 4702.920183] wlan0: deauthenticating from 00:02:6f:54:75:2f by local choice (reason=3)
Sep  8 23:29:25 alex-laptop wpa_supplicant[900]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep  8 23:29:25 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Sep  8 23:29:26 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep  8 23:29:29 alex-laptop wpa_supplicant[900]: Trying to associate with 00:02:6f:54:75:2f (SSID='WiFi' freq=2447 MHz)
Sep  8 23:29:29 alex-laptop kernel: [ 4706.195806] wlan0: direct probe to AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:29 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep  8 23:29:29 alex-laptop kernel: [ 4706.198462] wlan0: direct probe responded
Sep  8 23:29:29 alex-laptop kernel: [ 4706.198471] wlan0: authenticate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:29 alex-laptop kernel: [ 4706.200294] wlan0: authenticated
Sep  8 23:29:29 alex-laptop kernel: [ 4706.200335] wlan0: associate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:29 alex-laptop kernel: [ 4706.202401] wlan0: RX AssocResp from 00:02:6f:54:75:2f (capab=0x411 status=12 aid=1)
Sep  8 23:29:29 alex-laptop kernel: [ 4706.202409] wlan0: AP denied association (code=12)
Sep  8 23:29:29 alex-laptop kernel: [ 4706.202438] wlan0: deauthenticating from 00:02:6f:54:75:2f by local choice (reason=3)
Sep  8 23:29:30 alex-laptop NetworkManager: <debug> [1283984970.002358] periodic_update(): Roamed from BSSID 00:02:6F:54:75:2F (WiFi) to (none) ((none))
Sep  8 23:29:39 alex-laptop wpa_supplicant[900]: Authentication with 00:02:6f:54:75:2f timed out.
Sep  8 23:29:39 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Sep  8 23:29:39 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 4106
Sep  8 23:29:41 alex-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Sep  8 23:29:41 alex-laptop avahi-daemon[898]: Withdrawing address record for 192.168.1.69 on wlan0.
Sep  8 23:29:41 alex-laptop avahi-daemon[898]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.69.
Sep  8 23:29:41 alex-laptop avahi-daemon[898]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto WiFi'
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto WiFi' has security, and secrets exist.  No new secrets needed.
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Config: added 'ssid' value 'WiFi'
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep  8 23:29:41 alex-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  8 23:29:41 alex-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Sep  8 23:29:41 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep  8 23:29:41 alex-laptop wpa_supplicant[900]: Failed to initiate AP scan.
Sep  8 23:29:42 alex-laptop wpa_supplicant[900]: Trying to associate with 00:02:6f:54:75:2f (SSID='WiFi' freq=2447 MHz)
Sep  8 23:29:42 alex-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep  8 23:29:42 alex-laptop kernel: [ 4719.322960] wlan0: direct probe to AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:42 alex-laptop kernel: [ 4719.325646] wlan0: direct probe responded
Sep  8 23:29:42 alex-laptop kernel: [ 4719.325656] wlan0: authenticate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:42 alex-laptop kernel: [ 4719.327357] wlan0: authenticated
Sep  8 23:29:42 alex-laptop kernel: [ 4719.327403] wlan0: associate with AP 00:02:6f:54:75:2f (try 1)
Sep  8 23:29:42 alex-laptop kernel: [ 4719.329520] wlan0: RX AssocResp from 00:02:6f:54:75:2f (capab=0x411 status=12 aid=1)
Sep  8 23:29:42 alex-laptop kernel: [ 4719.329529] wlan0: AP denied association (code=12)
Sep  8 23:29:42 alex-laptop kernel: [ 4719.329559] wlan0: deauthenticating from 00:02:6f:54:75:2f by local choice (reason=3)

---

### Post by n00ne on 2011-06-17
I had exactly the same issue on Lucid with Intel WiFi Link 5100.
This is a weird issue since it never happened before (on this network which I haven't used in almost a year ) and never happened to me in any other network.
I saw some solutions online for maybe similar problems which suggested to change NM to WICD. but I didn't want to change my network manager for just one network. 
So I first tried to change the wireless security settings from only TKIP to use both TKIP and AES ( I guess if you don't have this option you can use AES only) and it's now seems to be working without any disconnects. I guess there is some bug with the NM and TKIP.
it's a bit sad because I think TKIP is a bit more secure then AES.

---

