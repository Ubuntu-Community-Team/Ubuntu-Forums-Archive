---
title: "no WLAN authentication with WPA(TKIP) router"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Rschnauzer on 2009-12-07
Hallo,

I was not able to define WPA(TKIP) in network manager for my wireless connection.
If i use WPA&WPA2 Personal the adapter dont get a valid authentication.
[COLOR=Blue]wpa_supplicant[1028]: Trying to associate with 00:1f:3f:a1:44:8e (SSID=... freq=2412 
wpa_supplicant[1028]: Association request to the driver failed
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating[/COLOR]
lsusb reports  [COLOR=Blue]13d3:3247 IMC Networks 802.11 n/g/b Wireless LAN Adapter[/COLOR] with an azurewav:* MAC address. 
I have to define WPA(TKIP) security in my router to support some old laptops.
Does anyone has a tip how to define networkmanager for WPA(TKIP)?

---

### Post by Rschnauzer on 2009-12-10
nobody able to help me?
I have fount some information about wpa_supplicant and added for testing 
/etc/wpa_supplicant/wpa_supplicant.conf
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="myssid"
    key_mgmt=WPA-PSK
    proto=WPA
    pairwise=TKIP
    group=TKIP
    psk="my63_bytes_secret_key"
}
But this does not work and the networkmanger still is not able to authenticate to the WLAN AP.
I do not unterstand, how things work together in Ubuntu. 

How may I define Ubuntu NetworkManager to connect to a WPA(TKIP) AP?

---

### Post by fubofo on 2009-12-20
Im also in a simlair situation with Kubuntu. Router set to WPA (TKIP) using a passphrase, though the network manager does not provide any option to set WPA to TKIP (only WPA-WPA2 Personal).

EDIT: seems to be a bug report filed  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432?comments=all)

---

### Post by swrightsls on 2009-12-20
I have the same problem - I've installed Ubuntu 9.10 on three older laptops for testing, and all of them have the same behaviour when attempting to connect to my access point, which is a Cisco (not linksys) 1100 series running in WPA/TKIP mode.
I can connect manually by choosing WPA/WPA2 personal when "connecting to hidden network" (the SSID is not broadcast) and entering the key, but after a reboot, the saved config will not work - it reverts back to WEP, and won't let me change profile to WPA.

All of these laptops dual boot to XP, and auto-reconnect to the same WPA/TKIP AP works just fine in XP. I was really hoping to get my kids using Linux, but I need the wireless to work correctly.

---

### Post by Rschnauzer on 2009-12-21
I did a wireshark trace on the WLAN activation, but it seems as if the authentification fails and a second try to a repeater fails to. There had been a lot of
[COLOR=Blue] 'MDNS standard query PTR_pgpkey-hkp._tcp.local, "QM" question' [/COLOR]
in the trace I had never seen before. (for testing I have an additional connection via eth0 to the router).

Following the messages from activation:
```
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) starting connection 'MYSSID'
Dec 21 17:29:03 MYPC NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 21 17:29:03 MYPC NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0/wireless): connection 'MYSSID' has security, and secrets exist.  No new secrets needed.
Dec 21 17:29:03 MYPC NetworkManager: <info>  Config: added 'ssid' value 'MYSSID'
Dec 21 17:29:03 MYPC NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 21 17:29:03 MYPC NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 21 17:29:03 MYPC NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec 21 17:29:03 MYPC NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 21 17:29:03 MYPC NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 21 17:29:03 MYPC NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 21 17:29:03 MYPC NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 21 17:29:03 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Dec 21 17:29:04 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:29:04 MYPC wpa_supplicant[1017]: WPS-AP-AVAILABLE 
Dec 21 17:29:04 MYPC wpa_supplicant[1017]: Trying to associate with 00:15:0c:ab:cd:ef (SSID='MYSSID' freq=2412 MHz)
Dec 21 17:29:04 MYPC wpa_supplicant[1017]: Association request to the driver failed
Dec 21 17:29:04 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 21 17:29:04 MYPC kernel: [  855.289407] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Dec 21 17:29:04 MYPC kernel: [  855.291041] wlan0: authenticated
Dec 21 17:29:04 MYPC kernel: [  855.291044] wlan0: associate with AP 00:15:0c:ab:cd:ef
Dec 21 17:29:04 MYPC kernel: [  855.296663] wlan0: RX AssocResp from 00:15:0c:ab:cd:ef (capab=0x451 status=0 aid=2)
Dec 21 17:29:04 MYPC kernel: [  855.296666] wlan0: associated
Dec 21 17:29:04 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Dec 21 17:29:04 MYPC wpa_supplicant[1017]: Associated with 00:15:0c:ab:cd:ef
Dec 21 17:29:04 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec 21 17:29:04 MYPC kernel: [  855.305752] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 21 17:29:05 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec 21 17:29:05 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Dec 21 17:29:05 MYPC wpa_supplicant[1017]: WPA: Key negotiation completed with 00:15:0c:ab:cd:ef [PTK=TKIP GTK=TKIP]
Dec 21 17:29:05 MYPC wpa_supplicant[1017]: CTRL-EVENT-CONNECTED - Connection to 00:15:0c:ab:cd:ef completed (auth) [id=0 id_str=]
Dec 21 17:29:05 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MYSSID'.
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 21 17:29:05 MYPC NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Dec 21 17:29:05 MYPC dhclient: Internet Systems Consortium DHCP Client V3.1.2
Dec 21 17:29:05 MYPC dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 21 17:29:05 MYPC dhclient: All rights reserved.
Dec 21 17:29:05 MYPC dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 21 17:29:05 MYPC dhclient: 
Dec 21 17:29:05 MYPC NetworkManager: <info>  dhclient started with pid 2625
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Dec 21 17:29:05 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec 21 17:29:05 MYPC NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Dec 21 17:29:06 MYPC dhclient: Listening on LPF/wlan0/00:15:af:ab:cd:ef
Dec 21 17:29:06 MYPC dhclient: Sending on   LPF/wlan0/00:15:af:ab:cd:ef
Dec 21 17:29:06 MYPC dhclient: Sending on   Socket/fallback
Dec 21 17:29:06 MYPC avahi-daemon[762]: Registering new address record for fe80::215:afff:fe44:39c8 on wlan0.*.
Dec 21 17:29:09 MYPC dhclient: DHCPREQUEST of 192.168.xxx.21 on wlan0 to 255.255.255.255 port 67
Dec 21 17:29:09 MYPC dhclient: DHCPNAK from 192.168.xxx.1
Dec 21 17:29:09 MYPC NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> expire
Dec 21 17:29:09 MYPC NetworkManager: <info>  DHCP: device wlan0 state changed expire -> preinit
Dec 21 17:29:09 MYPC dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 21 17:29:15 MYPC dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Dec 21 17:29:15 MYPC dhclient: DHCPOFFER of 192.168.xxx.21 from 192.168.xxx.1
Dec 21 17:29:15 MYPC dhclient: DHCPREQUEST of 192.168.xxx.21 on wlan0 to 255.255.255.255 port 67
Dec 21 17:29:15 MYPC dhclient: DHCPACK of 192.168.xxx.21 from 192.168.xxx.1
Dec 21 17:29:15 MYPC dhclient: bound to 192.168.xxx.21 -- renewal in 379229 seconds.
Dec 21 17:29:15 MYPC NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Dec 21 17:29:15 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 21 17:29:15 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 21 17:29:15 MYPC NetworkManager: <info>    address 192.168.xxx.21
Dec 21 17:29:15 MYPC NetworkManager: <info>    prefix 24 (255.255.255.0)
Dec 21 17:29:15 MYPC NetworkManager: <info>    gateway 192.168.xxx.1
Dec 21 17:29:15 MYPC NetworkManager: <info>    nameserver '192.168.xxx.1'
Dec 21 17:29:15 MYPC NetworkManager: <info>    domain name 'fritz.box'
Dec 21 17:29:15 MYPC NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec 21 17:29:15 MYPC NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 21 17:29:15 MYPC NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 21 17:29:15 MYPC avahi-daemon[762]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.xxx.21.
Dec 21 17:29:15 MYPC avahi-daemon[762]: New relevant interface wlan0.IPv4 for mDNS.
Dec 21 17:29:15 MYPC avahi-daemon[762]: Registering new address record for 192.168.xxx.21 on wlan0.IPv4.
Dec 21 17:29:15 MYPC kernel: [  866.100007] wlan0: no IPv6 routers present
Dec 21 17:29:16 MYPC NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 21 17:29:16 MYPC NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Dec 21 17:29:16 MYPC NetworkManager: <debug> [1261412956.069065] periodic_update(): Roamed from BSSID 00:1F:3F:ab:cd:ef (MYSSID) to 00:15:0C:ab:cd:ef (MYSSID)
Dec 21 17:29:16 MYPC NetworkManager: <info>  Activation (wlan0) successful, device activated.
Dec 21 17:29:16 MYPC NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 21 17:29:17 MYPC ntpd[1760]: ntpd exiting on signal 15
Dec 21 17:29:17 MYPC ntpdate[2708]: adjust time server 91.189.94.4 offset -0.025591 sec
Dec 21 17:29:17 MYPC ntpd[2736]: ntpd 4.2.4p6@1.1549-o Fri Dec  4 19:03:28 UTC 2009 (1)
Dec 21 17:29:17 MYPC ntpd[2737]: precision = 1.000 usec
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #1 wildcard, ::#123 Disabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #2 lo, ::1#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #3 eth0, fe80::21d:92ff:fe24:4f1c#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #4 wlan0, fe80::215:afff:fe44:39c8#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #6 eth0, 192.168.xxx.22#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: Listening on interface #7 wlan0, 192.168.xxx.21#123 Enabled
Dec 21 17:29:17 MYPC ntpd[2737]: kernel time sync status 2040
Dec 21 17:29:17 MYPC ntpd[2737]: frequency initialized -63.547 PPM from /var/lib/ntp/ntp.drift
Dec 21 17:29:29 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:30:09 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:31:09 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:32:29 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:32:46 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:46 MYPC kernel: [ 1076.502071] wlan0: deauthenticated (Reason: 7)
Dec 21 17:32:46 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Dec 21 17:32:46 MYPC kernel: [ 1076.530048] wlan0 direct probe responded
Dec 21 17:32:46 MYPC kernel: [ 1076.530052] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Dec 21 17:32:46 MYPC kernel: [ 1076.531569] wlan0: authenticated
Dec 21 17:32:46 MYPC kernel: [ 1076.531571] wlan0: associate with AP 00:15:0c:ab:cd:ef
Dec 21 17:32:46 MYPC kernel: [ 1076.536573] wlan0: RX ReassocResp from 00:15:0c:ab:cd:ef (capab=0x451 status=0 aid=2)
Dec 21 17:32:46 MYPC kernel: [ 1076.536576] wlan0: associated
Dec 21 17:32:46 MYPC wpa_supplicant[1017]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Dec 21 17:32:46 MYPC wpa_supplicant[1017]: Associated with 00:15:0c:ab:cd:ef
Dec 21 17:32:46 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Dec 21 17:32:47 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Dec 21 17:32:50 MYPC wpa_supplicant[1017]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Dec 21 17:32:50 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:50 MYPC kernel: [ 1080.534260] wlan0: deauthenticated (Reason: 1)
Dec 21 17:32:50 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec 21 17:32:50 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 21 17:32:51 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:51 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Dec 21 17:32:51 MYPC kernel: [ 1081.531264] wlan0: direct probe to AP 00:15:0c:ab:cd:ef try 1
Dec 21 17:32:51 MYPC kernel: [ 1081.533429] wlan0 direct probe responded
Dec 21 17:32:51 MYPC kernel: [ 1081.533432] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Dec 21 17:32:51 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:52 MYPC wpa_supplicant[1017]: last message repeated 5 times
Dec 21 17:32:52 MYPC kernel: [ 1082.531259] wlan0: direct probe to AP 00:15:0c:ab:cd:ef try 1
Dec 21 17:32:52 MYPC kernel: [ 1082.533227] wlan0 direct probe responded
Dec 21 17:32:52 MYPC kernel: [ 1082.533229] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Dec 21 17:32:52 MYPC kernel: [ 1082.537348] wlan0: authenticated
Dec 21 17:32:52 MYPC kernel: [ 1082.537350] wlan0: associate with AP 00:15:0c:ab:cd:ef
Dec 21 17:32:52 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> 4-way handshake
Dec 21 17:32:52 MYPC wpa_supplicant[1017]: Associated with 00:15:0c:ab:cd:ef
Dec 21 17:32:52 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Dec 21 17:32:52 MYPC kernel: [ 1082.560663] wlan0: RX ReassocResp from 00:15:0c:ab:cd:ef (capab=0x451 status=0 aid=2)
Dec 21 17:32:52 MYPC kernel: [ 1082.560667] wlan0: associated
Dec 21 17:32:54 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:32:54 MYPC wpa_supplicant[1017]: Trying to associate with 00:1f:3f:ab:cd:ef (SSID='MYSSID' freq=2412 MHz)
Dec 21 17:32:54 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> associating
Dec 21 17:32:54 MYPC wpa_supplicant[1017]: Association request to the driver failed
Dec 21 17:32:54 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:54 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 21 17:32:54 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> 4-way handshake
Dec 21 17:32:55 MYPC NetworkManager: <debug> [1261413175.001160] periodic_update(): Roamed from BSSID 00:15:0C:ab:cd:ef (MYSSID) to (none) ((none))
Dec 21 17:32:55 MYPC kernel: [ 1086.207770] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 1
Dec 21 17:32:56 MYPC kernel: [ 1086.400008] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 2
Dec 21 17:32:56 MYPC kernel: [ 1086.605509] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 3
Dec 21 17:32:56 MYPC wpa_supplicant[1017]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Dec 21 17:32:56 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:56 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Dec 21 17:32:56 MYPC kernel: [ 1086.800007] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef timed out
Dec 21 17:32:56 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 21 17:32:58 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:32:58 MYPC wpa_supplicant[1017]: WPS-AP-AVAILABLE 
Dec 21 17:32:58 MYPC wpa_supplicant[1017]: Trying to associate with 00:1f:3f:ab:cd:ef (SSID='MYSSID' freq=2412 MHz)
Dec 21 17:32:58 MYPC wpa_supplicant[1017]: Association request to the driver failed
Dec 21 17:32:58 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 21 17:32:58 MYPC kernel: [ 1088.519126] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 1
Dec 21 17:32:58 MYPC kernel: [ 1088.710012] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 2
Dec 21 17:32:58 MYPC kernel: [ 1088.910012] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef try 3
Dec 21 17:32:58 MYPC wpa_supplicant[1017]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 21 17:32:58 MYPC NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 21 17:32:58 MYPC kernel: [ 1089.110012] wlan0: direct probe to AP 00:1f:3f:ab:cd:ef timed out
Dec 21 17:33:01 MYPC NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Dec 21 17:33:01 MYPC NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Dec 21 17:33:01 MYPC NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2625
Dec 21 17:33:01 MYPC avahi-daemon[762]: Withdrawing address record for 192.168.xxx.21 on wlan0.
Dec 21 17:33:01 MYPC avahi-daemon[762]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.xxx.21.
Dec 21 17:33:01 MYPC avahi-daemon[762]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 21 17:33:01 MYPC NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 21 17:33:03 MYPC wpa_supplicant[1017]: Authentication with 00:00:00:00:00:00 timed out.
Dec 21 17:33:04 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:33:04 MYPC wpa_supplicant[1017]: WPS-AP-AVAILABLE 
Dec 21 17:33:04 MYPC wpa_supplicant[1017]: Trying to associate with 00:15:0c:ab:cd:ef (SSID='MYSSID' freq=2412 MHz)
Dec 21 17:33:04 MYPC wpa_supplicant[1017]: Association request to the driver failed
Dec 21 17:33:04 MYPC kernel: [ 1095.079182] wlan0: authenticate with AP 00:15:0c:ab:cd:ef
Dec 21 17:33:04 MYPC kernel: [ 1095.082317] wlan0: authenticated
Dec 21 17:33:04 MYPC kernel: [ 1095.082320] wlan0: associate with AP 00:15:0c:ab:cd:ef
Dec 21 17:33:04 MYPC kernel: [ 1095.085688] wlan0: RX ReassocResp from 00:15:0c:ab:cd:ef (capab=0x451 status=0 aid=2)
Dec 21 17:33:04 MYPC kernel: [ 1095.085691] wlan0: associated
Dec 21 17:33:04 MYPC wpa_supplicant[1017]: Associated with 00:15:0c:ab:cd:ef
Dec 21 17:33:05 MYPC wpa_supplicant[1017]: WPA: Key negotiation completed with 00:15:0c:ab:cd:ef [PTK=TKIP GTK=TKIP]
Dec 21 17:33:05 MYPC wpa_supplicant[1017]: CTRL-EVENT-CONNECTED - Connection to 00:15:0c:ab:cd:ef completed (reauth) [id=0 id_str=]
Dec 21 17:33:31 MYPC ntpd[2737]: synchronized to 91.189.94.4, stratum 2
Dec 21 17:33:31 MYPC ntpd[2737]: kernel time sync status change 2001
Dec 21 17:34:09 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:34:18 MYPC ntpd[2737]: Deleting interface #7 wlan0, 192.168.xxx.21#123, interface stats: received=0, sent=0, dropped=0, active_time=301 secs
Dec 21 17:36:09 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS 
Dec 21 17:38:09 MYPC wpa_supplicant[1017]: CTRL-EVENT-SCAN-RESULTS  
```Does anybody know what to do, to connect to the AP?
(edit)
I again did a try to solve the problem:
After booting the PC the adapter connects to the AP. 
NetworkManager displays an active network connection with driver rt2800usb WPA/WPA2 security.
DHCP assigned a valid IP-address, but the router (FritzBox) does not show the connection.
In wireshark some traffic is displayed, ping to the router is successful, but access via browser to the router is not possible.
After a while the connection is lost, and in wireshark some EAPOL frames go between client and AP.
In windows the name of the driver is rt287xusb, is rt2800usb the correct driver in Ubuntu?

---

