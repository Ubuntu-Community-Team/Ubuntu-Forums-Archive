---
title: "Jaunty wireless issues"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2009-04-20
I've upgraded to the Jaunty beta, and I am all of a sudden having problems with the ipw2200 driver.  It is intermittently dropping connection then re-establishing.


At the time of the drop, in /var/log/messages the only thing I see is:

ipw2200: Firmware error detected.  Restarting.

and at the same time in the syslog is this:
```

Apr 20 10:21:10 miata NetworkManager: <info>  (eth1): supplicant connection state:  completed -> associating 
Apr 20 10:21:11 miata NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected 
Apr 20 10:21:11 miata NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associated 
Apr 20 10:21:12 miata kernel: [ 4582.856065] ipw2200: Failed to send SYSTEM_CONFIG: Command timed out.
Apr 20 10:21:13 miata NetworkManager: <debug> [1240237273.001808] periodic_update(): Roamed from BSSID 00:14:1B:5A:29:11 (PSC) to 00:14:1B:5A:2A:21 (PSC) 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): deactivating device (reason: 11). 
Apr 20 10:21:26 miata NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 4585 
Apr 20 10:21:26 miata NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Apr 20 10:21:26 miata avahi-daemon[3104]: Withdrawing address record for x.x.x.x on eth1.
Apr 20 10:21:26 miata avahi-daemon[3104]: Leaving mDNS multicast group on interface eth1.IPv4 with address x.x.x.x.
Apr 20 10:21:26 miata avahi-daemon[3104]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) starting connection 'PSC' 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1/wireless): connection 'PSC' has security, and secrets exist.  No new secrets needed. 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'ssid' value 'PSC' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-EAP' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'eap' value 'TLS' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'ca_cert' value 'blob://-org-freedesktop-NetworkManagerSettings-2-ca_cert' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'private_key' value 'blob://-org-freedesktop-NetworkManagerSettings-2-private_key' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'client_cert' value 'blob://-org-freedesktop-NetworkManagerSettings-2-client_cert' 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: added 'identity' value 'miata.nowhere.com' 
Apr 20 10:21:26 miata NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected 
Apr 20 10:21:26 miata NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 20 10:21:26 miata NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Apr 20 10:21:26 miata nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 20 10:21:27 miata NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Apr 20 10:21:27 miata NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Apr 20 10:21:27 miata NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Apr 20 10:21:27 miata NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> disconnected 
Apr 20 10:21:27 miata NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Apr 20 10:21:28 miata NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Apr 20 10:21:30 miata NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Apr 20 10:21:31 miata kernel: [ 4602.680052] ipw2200: Failed to send SYSTEM_CONFIG: Command timed out.
Apr 20 10:21:42 miata NetworkManager: <info>  eth1: link timed out. 
Apr 20 10:21:53 miata kernel: [ 4624.366879] ipw2200: Firmware error detected.  Restarting.
Apr 20 10:21:54 miata NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected 
Apr 20 10:21:54 miata NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed 
Apr 20 10:21:55 miata NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PSC'. 
Apr 20 10:21:55 miata NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 20 10:21:55 miata NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Apr 20 10:21:55 miata NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Apr 20 10:21:55 miata NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Apr 20 10:21:55 miata dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 20 10:21:55 miata dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 20 10:21:55 miata dhclient: All rights reserved.
Apr 20 10:21:55 miata dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 20 10:21:55 miata dhclient: 
Apr 20 10:21:55 miata NetworkManager: <info>  dhclient started with pid 10995 
Apr 20 10:21:55 miata NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Apr 20 10:21:55 miata NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Apr 20 10:21:55 miata dhclient: Listening on LPF/eth1/00:15:00:3e:b3:28
Apr 20 10:21:55 miata dhclient: Sending on   LPF/eth1/00:15:00:3e:b3:28
Apr 20 10:21:55 miata dhclient: Sending on   Socket/fallback
Apr 20 10:21:58 miata dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 20 10:21:58 miata dhclient: DHCPOFFER of x.x.x.x from x.x.x.x
Apr 20 10:21:58 miata dhclient: DHCPREQUEST of x.x.x.x on eth1 to 255.255.255.255 port 67
Apr 20 10:21:58 miata dhclient: DHCPACK of x.x.x.x from x.x.x.x
Apr 20 10:21:58 miata NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Apr 20 10:21:58 miata NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 20 10:21:58 miata NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Apr 20 10:21:58 miata NetworkManager: <info>    address x.x.x.x 
Apr 20 10:21:58 miata NetworkManager: <info>    prefix 23 (255.255.254.0) 
Apr 20 10:21:58 miata NetworkManager: <info>    gateway x.x.x.x 
Apr 20 10:21:58 miata NetworkManager: <info>    hostname 'miata.nowhere.com' 
Apr 20 10:21:58 miata NetworkManager: <info>    nameserver 'x.x.x.x' 
Apr 20 10:21:58 miata NetworkManager: <info>    nameserver 'x.x.x.x' 
Apr 20 10:21:58 miata NetworkManager: <info>    nameserver 'x.x.x.x' 
Apr 20 10:21:58 miata NetworkManager: <info>    domain name 'nowhere.com' 
Apr 20 10:21:58 miata dhclient: bound to x.x.x.x -- renewal in 39722 seconds.
Apr 20 10:21:58 miata NetworkManager: <info>    wins 'x.x.x.x' 
Apr 20 10:21:58 miata NetworkManager: <info>    wins 'x.x.x.x' 
Apr 20 10:21:58 miata NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 20 10:21:58 miata NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Apr 20 10:21:58 miata NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Apr 20 10:21:58 miata avahi-daemon[3104]: Joining mDNS multicast group on interface eth1.IPv4 with address x.x.x.x.
Apr 20 10:21:58 miata avahi-daemon[3104]: New relevant interface eth1.IPv4 for mDNS.
Apr 20 10:21:58 miata avahi-daemon[3104]: Registering new address record for x.x.x.x on eth1.IPv4.
Apr 20 10:21:59 miata NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Apr 20 10:21:59 miata NetworkManager: <debug> [1240237319.380982] periodic_update(): Roamed from BSSID 00:14:1B:5A:2A:21 (PSC) to 00:14:1B:5E:29:11 (PSC) 
Apr 20 10:21:59 miata NetworkManager: <info>  Policy set 'PSC' (eth1) as default for routing and DNS. 
Apr 20 10:21:59 miata NetworkManager: <info>  Activation (eth1) successful, device activated. 
Apr 20 10:21:59 miata NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 20 10:22:01 miata ntpdate[11218]: adjust time server x.x.x.x offset -0.008594 sec
```

Any thoughts or more info I can give?
-J

---

