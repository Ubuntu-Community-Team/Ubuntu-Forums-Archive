---
title: "Wireless Card Times Out Every Time"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by WarholsGhost on 2009-05-28
Hello,

So i have this problem with an access point, My wireless card fails to connect to it but my wife's computer's card connects perfectly. How can i solve this? below are the syslog for both cards:

This is the internal wireless card on my computer:
```
May 28 07:38:58 emma NetworkManager: <info>  ActivatiMay 28 07:53:01 emma kernel: [ 4742.960034] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
May 28 07:53:01 emma kernel: [ 4742.960044] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
May 28 07:53:01 emma kernel: [ 4742.977250] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
May 28 07:53:01 emma kernel: [ 4743.050929] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May 28 07:53:01 emma kernel: [ 4743.056404] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May 28 07:53:02 emma kernel: [ 4743.324329] eth2: Hardware identity 800c:0000:0001:0000
May 28 07:53:02 emma kernel: [ 4743.324482] eth2: Station identity  001f:0005:0001:0003
May 28 07:53:02 emma kernel: [ 4743.324486] eth2: Firmware determined as Intersil 1.3.5
May 28 07:53:02 emma kernel: [ 4743.324488] eth2: Ad-hoc demo mode supported
May 28 07:53:02 emma kernel: [ 4743.324490] eth2: IEEE standard IBSS ad-hoc mode supported
May 28 07:53:02 emma kernel: [ 4743.324492] eth2: WEP supported, 104-bit key
May 28 07:53:02 emma kernel: [ 4743.464131] eth2: MAC address 00:20:e0:88:42:a3
May 28 07:53:02 emma kernel: [ 4743.464270] eth2: Station name "Prism  I"
May 28 07:53:02 emma kernel: [ 4743.464783] eth2: ready
May 28 07:53:02 emma kernel: [ 4743.465800] eth2: orinoco_cs at 0.0, irq 3, io 0x3100-0x313f
May 28 07:53:02 emma nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_20_e0_88_42_a3, iface: eth2): not well known
May 28 07:53:02 emma NetworkManager: <info>  (eth2): driver does not support SSID scans (scan_capa 0x00). 
May 28 07:53:02 emma NetworkManager: <info>  (eth2): new 802.11 WiFi device (driver: 'orinoco_cs') 
May 28 07:53:02 emma NetworkManager: <info>  (eth2): exported as /org/freedesktop/Hal/devices/net_00_20_e0_88_42_a3 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): device state change: 1 -> 2 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): bringing up device. 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): preparing device. 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): deactivating device (reason: 2). 
May 28 07:53:07 emma kernel: [ 4748.168479] ADDRCONF(NETDEV_UP): eth2: link is not ready
May 28 07:53:07 emma kernel: [ 4748.181549] eth2: New link status: Disconnected (0002)
May 28 07:53:07 emma NetworkManager: <info>  (eth2): device state change: 2 -> 3 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): supplicant interface state:  starting -> ready 
May 28 07:53:09 emma kernel: [ 4750.732609] eth2: New link status: Connected (0001)
May 28 07:53:09 emma kernel: [ 4750.732654] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
May 28 07:53:10 emma avahi-daemon[4646]: Registering new address record for fe80::220:e0ff:fe88:42a3 on eth2.*.
May 28 07:53:19 emma kernel: [ 4760.788022] eth2: no IPv6 routers present
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) starting connection 'Auto linksys' 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 3 -> 4 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 4 -> 5 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2/wireless): access point 'Auto linksys' has security, but secrets are required. 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 5 -> 6 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): device state change: 6 -> 4 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): device state change: 4 -> 5 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2/wireless): connection 'Auto linksys' has security, and secrets exist.  No new secrets needed. 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'ssid' value 'linksys' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
May 28 07:53:32 emma NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:53:32 emma NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Config: set interface ap_scan to 1 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): supplicant connection state:  scanning -> disconnected 
May 28 07:53:33 emma NetworkManager: <info>  (eth2): supplicant connection state:  disconnected -> scanning 
May 28 07:53:34 emma kernel: [ 4775.373990] eth2: New link status: Disconnected (0002)
May 28 07:53:34 emma NetworkManager: <info>  (eth2): supplicant connection state:  scanning -> associating 
May 28 07:53:34 emma NetworkManager: <info>  (eth2): supplicant connection state:  associating -> disconnected 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): supplicant connection state:  disconnected -> associated 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): supplicant connection state:  associated -> completed 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): device state change: 5 -> 7 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction. 
May 28 07:53:35 emma dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 28 07:53:35 emma dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 28 07:53:35 emma dhclient: All rights reserved.
May 28 07:53:35 emma dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 28 07:53:35 emma kernel: [ 4776.276788] eth2: New link status: Connected (0001)
May 28 07:53:35 emma dhclient: 
May 28 07:53:35 emma NetworkManager: <info>  dhclient started with pid 13169 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 28 07:53:35 emma NetworkManager: <info>  DHCP: device eth2 state changed (null) -> preinit 
May 28 07:53:35 emma dhclient: Listening on LPF/eth2/00:20:e0:88:42:a3
May 28 07:53:35 emma dhclient: Sending on   LPF/eth2/00:20:e0:88:42:a3
May 28 07:53:35 emma dhclient: Sending on   Socket/fallback
May 28 07:53:35 emma dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
May 28 07:53:35 emma dhclient: DHCPOFFER of 192.168.1.104 from 192.168.1.1
May 28 07:53:35 emma dhclient: DHCPREQUEST of 192.168.1.104 on eth2 to 255.255.255.255 port 67
May 28 07:53:35 emma dhclient: DHCPACK of 192.168.1.104 from 192.168.1.1
May 28 07:53:35 emma NetworkManager: <info>  DHCP: device eth2 state changed preinit -> bound 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) scheduled... 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) started... 
May 28 07:53:35 emma NetworkManager: <info>    address 192.168.1.104 
May 28 07:53:35 emma NetworkManager: <info>    prefix 24 (255.255.255.0) 
May 28 07:53:35 emma NetworkManager: <info>    gateway 192.168.1.1 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.76.178' 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.78.130' 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.69.146' 
May 28 07:53:35 emma NetworkManager: <info>    domain name 'hsd1.ca.comcast.net.' 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) complete. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 28 07:53:35 emma avahi-daemon[4646]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.1.104.
May 28 07:53:35 emma avahi-daemon[4646]: New relevant interface eth2.IPv4 for mDNS.
May 28 07:53:35 emma avahi-daemon[4646]: Registering new address record for 192.168.1.104 on eth2.IPv4.
May 28 07:53:35 emma dhclient: bound to 192.168.1.104 -- renewal in 40541 seconds.
May 28 07:53:36 emma NetworkManager: <info>  (eth2): device state change: 7 -> 8 
May 28 07:53:36 emma NetworkManager: <info>  Policy set 'Auto linksys' (eth2) as default for routing and DNS. 
May 28 07:53:36 emma NetworkManager: <info>  Activation (eth2) successful, device activated. 
May 28 07:53:36 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 28 07:53:37 emma ntpdate[13232]: adjust time server 91.189.94.4 offset -0.011140 secon (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): device state change: 6 -> 4 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0/wireless): connection 'Auto linksys' has security, and secrets exist.  No new secrets needed. 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'ssid' value 'linksys' 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May 28 07:38:58 emma NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
May 28 07:38:58 emma NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:38:58 emma NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 28 07:38:58 emma NetworkManager: <info>  Config: set interface ap_scan to 1 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  completed -> disconnected 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  disconnected -> scanning 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  scanning -> disconnected 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  disconnected -> associating 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  associating -> associated 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): supplicant connection state:  associated -> completed 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'. 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 28 07:38:58 emma NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 28 07:38:58 emma dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 28 07:38:58 emma dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 28 07:38:58 emma dhclient: All rights reserved.
May 28 07:38:58 emma dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 28 07:38:58 emma dhclient: 
May 28 07:38:58 emma NetworkManager: <info>  dhclient started with pid 12498 
May 28 07:38:58 emma NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 28 07:38:58 emma NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 28 07:38:58 emma dhclient: Listening on LPF/eth0/00:15:00:36:ee:38
May 28 07:38:58 emma dhclient: Sending on   LPF/eth0/00:15:00:36:ee:38
May 28 07:38:58 emma dhclient: Sending on   Socket/fallback
May 28 07:38:58 emma dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 28 07:39:04 emma dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 28 07:39:17 emma dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 28 07:39:30 emma dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 28 07:39:42 emma dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 28 07:39:44 emma NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
May 28 07:39:44 emma NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 12498 
May 28 07:39:44 emma NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 28 07:39:44 emma NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
May 28 07:39:44 emma NetworkManager: <info>  Activation (eth0/wireless): could not get IP configuration for connection 'Auto linksys'. 
May 28 07:39:44 emma NetworkManager: <info>  (eth0): device state change: 7 -> 6 
May 28 07:39:44 emma NetworkManager: <info>  Activation (eth0/wireless): asking for new secrets 
May 28 07:39:44 emma NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 


```

and on my wife's computer, with the same access point:
```
May 28 07:53:01 emma kernel: [ 4742.960034] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
May 28 07:53:01 emma kernel: [ 4742.960044] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
May 28 07:53:01 emma kernel: [ 4742.977250] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
May 28 07:53:01 emma kernel: [ 4743.050929] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May 28 07:53:01 emma kernel: [ 4743.056404] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
May 28 07:53:02 emma kernel: [ 4743.324329] eth2: Hardware identity 800c:0000:0001:0000
May 28 07:53:02 emma kernel: [ 4743.324482] eth2: Station identity  001f:0005:0001:0003
May 28 07:53:02 emma kernel: [ 4743.324486] eth2: Firmware determined as Intersil 1.3.5
May 28 07:53:02 emma kernel: [ 4743.324488] eth2: Ad-hoc demo mode supported
May 28 07:53:02 emma kernel: [ 4743.324490] eth2: IEEE standard IBSS ad-hoc mode supported
May 28 07:53:02 emma kernel: [ 4743.324492] eth2: WEP supported, 104-bit key
May 28 07:53:02 emma kernel: [ 4743.464131] eth2: MAC address 00:20:e0:88:42:a3
May 28 07:53:02 emma kernel: [ 4743.464270] eth2: Station name "Prism  I"
May 28 07:53:02 emma kernel: [ 4743.464783] eth2: ready
May 28 07:53:02 emma kernel: [ 4743.465800] eth2: orinoco_cs at 0.0, irq 3, io 0x3100-0x313f
May 28 07:53:02 emma nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_20_e0_88_42_a3, iface: eth2): not well known
May 28 07:53:02 emma NetworkManager: <info>  (eth2): driver does not support SSID scans (scan_capa 0x00). 
May 28 07:53:02 emma NetworkManager: <info>  (eth2): new 802.11 WiFi device (driver: 'orinoco_cs') 
May 28 07:53:02 emma NetworkManager: <info>  (eth2): exported as /org/freedesktop/Hal/devices/net_00_20_e0_88_42_a3 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): device state change: 1 -> 2 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): bringing up device. 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): preparing device. 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): deactivating device (reason: 2). 
May 28 07:53:07 emma kernel: [ 4748.168479] ADDRCONF(NETDEV_UP): eth2: link is not ready
May 28 07:53:07 emma kernel: [ 4748.181549] eth2: New link status: Disconnected (0002)
May 28 07:53:07 emma NetworkManager: <info>  (eth2): device state change: 2 -> 3 
May 28 07:53:07 emma NetworkManager: <info>  (eth2): supplicant interface state:  starting -> ready 
May 28 07:53:09 emma kernel: [ 4750.732609] eth2: New link status: Connected (0001)
May 28 07:53:09 emma kernel: [ 4750.732654] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
May 28 07:53:10 emma avahi-daemon[4646]: Registering new address record for fe80::220:e0ff:fe88:42a3 on eth2.*.
May 28 07:53:19 emma kernel: [ 4760.788022] eth2: no IPv6 routers present
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) starting connection 'Auto linksys' 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 3 -> 4 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 4 -> 5 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2/wireless): access point 'Auto linksys' has security, but secrets are required. 
May 28 07:53:28 emma NetworkManager: <info>  (eth2): device state change: 5 -> 6 
May 28 07:53:28 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): device state change: 6 -> 4 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): device state change: 4 -> 5 
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2/wireless): connection 'Auto linksys' has security, and secrets exist.  No new secrets needed. 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'ssid' value 'linksys' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May 28 07:53:32 emma NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
May 28 07:53:32 emma NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:53:32 emma NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 28 07:53:32 emma NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
May 28 07:53:32 emma NetworkManager: <info>  Config: set interface ap_scan to 1 
May 28 07:53:32 emma NetworkManager: <info>  (eth2): supplicant connection state:  scanning -> disconnected 
May 28 07:53:33 emma NetworkManager: <info>  (eth2): supplicant connection state:  disconnected -> scanning 
May 28 07:53:34 emma kernel: [ 4775.373990] eth2: New link status: Disconnected (0002)
May 28 07:53:34 emma NetworkManager: <info>  (eth2): supplicant connection state:  scanning -> associating 
May 28 07:53:34 emma NetworkManager: <info>  (eth2): supplicant connection state:  associating -> disconnected 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): supplicant connection state:  disconnected -> associated 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): supplicant connection state:  associated -> completed 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) started... 
May 28 07:53:35 emma NetworkManager: <info>  (eth2): device state change: 5 -> 7 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Beginning DHCP transaction. 
May 28 07:53:35 emma dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 28 07:53:35 emma dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 28 07:53:35 emma dhclient: All rights reserved.
May 28 07:53:35 emma dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 28 07:53:35 emma kernel: [ 4776.276788] eth2: New link status: Connected (0001)
May 28 07:53:35 emma dhclient: 
May 28 07:53:35 emma NetworkManager: <info>  dhclient started with pid 13169 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete. 
May 28 07:53:35 emma NetworkManager: <info>  DHCP: device eth2 state changed (null) -> preinit 
May 28 07:53:35 emma dhclient: Listening on LPF/eth2/00:20:e0:88:42:a3
May 28 07:53:35 emma dhclient: Sending on   LPF/eth2/00:20:e0:88:42:a3
May 28 07:53:35 emma dhclient: Sending on   Socket/fallback
May 28 07:53:35 emma dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
May 28 07:53:35 emma dhclient: DHCPOFFER of 192.168.1.104 from 192.168.1.1
May 28 07:53:35 emma dhclient: DHCPREQUEST of 192.168.1.104 on eth2 to 255.255.255.255 port 67
May 28 07:53:35 emma dhclient: DHCPACK of 192.168.1.104 from 192.168.1.1
May 28 07:53:35 emma NetworkManager: <info>  DHCP: device eth2 state changed preinit -> bound 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) scheduled... 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) started... 
May 28 07:53:35 emma NetworkManager: <info>    address 192.168.1.104 
May 28 07:53:35 emma NetworkManager: <info>    prefix 24 (255.255.255.0) 
May 28 07:53:35 emma NetworkManager: <info>    gateway 192.168.1.1 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.76.178' 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.78.130' 
May 28 07:53:35 emma NetworkManager: <info>    nameserver '68.87.69.146' 
May 28 07:53:35 emma NetworkManager: <info>    domain name 'hsd1.ca.comcast.net.' 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP Configure Get) complete. 
May 28 07:53:35 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) started... 
May 28 07:53:35 emma avahi-daemon[4646]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.1.104.
May 28 07:53:35 emma avahi-daemon[4646]: New relevant interface eth2.IPv4 for mDNS.
May 28 07:53:35 emma avahi-daemon[4646]: Registering new address record for 192.168.1.104 on eth2.IPv4.
May 28 07:53:35 emma dhclient: bound to 192.168.1.104 -- renewal in 40541 seconds.
May 28 07:53:36 emma NetworkManager: <info>  (eth2): device state change: 7 -> 8 
May 28 07:53:36 emma NetworkManager: <info>  Policy set 'Auto linksys' (eth2) as default for routing and DNS. 
May 28 07:53:36 emma NetworkManager: <info>  Activation (eth2) successful, device activated. 
May 28 07:53:36 emma NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) complete. 
May 28 07:53:37 emma ntpdate[13232]: adjust time server 91.189.94.4 offset -0.011140 sec

```

---

### Post by superprash2003 on 2009-05-28
similar to this?[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by WarholsGhost on 2009-05-28
sadly i tried what was suggested there and no help.

---

