---
title: "Lost network connection - hardware or software problem?"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by HilliBilly on 2011-11-17
one pc does not connect to the network anymore and i do not understand why. everything else works, i mean all other pcs, the whole network itself and the internet connection is up as well.

i changed the network cable already.

daemon.log

> 
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov 17 08:45:58 c4 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 17 08:45:58 c4 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 17 08:45:58 c4 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 17 08:45:58 c4 NetworkManager: <info>  dhclient started with pid 1682
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 17 08:45:58 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 17 08:45:58 c4 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Nov 17 08:45:58 c4 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Nov 17 08:45:58 c4 dhclient: All rights reserved.
Nov 17 08:45:58 c4 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Nov 17 08:45:58 c4 dhclient: 
Nov 17 08:45:58 c4 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Nov 17 08:45:58 c4 dhclient: Listening on LPF/eth0/00:1a:4d:53:1c:1d
Nov 17 08:45:58 c4 dhclient: Sending on   LPF/eth0/00:1a:4d:53:1c:1d
Nov 17 08:45:58 c4 dhclient: Sending on   Socket/fallback
Nov 17 08:45:58 c4 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Nov 17 08:46:01 c4 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 17 08:46:06 c4 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 17 08:46:15 c4 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov 17 08:46:35 c4 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 17 08:46:44 c4 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Nov 17 08:46:44 c4 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1682
Nov 17 08:46:44 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Nov 17 08:46:44 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Nov 17 08:46:44 c4 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Nov 17 08:46:44 c4 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Nov 17 08:46:44 c4 NetworkManager: <info>  Activation (eth0) failed.
Nov 17 08:46:44 c4 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Nov 17 08:46:44 c4 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Nov 17 08:46:44 c4 NetworkManager: <info>  (eth0): deactivating device (reason: 0).

---

