---
title: "WICD won't connect when my computer starts."
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by AgentOrange96 on 2013-02-01
My problem is quite simple. When I start my computer, WICD tries to connect to the network. (Both my school's and my home's.) It takes many minutes and fails. When I bring my computer out of sleep after a while, it doesn't even attempt to re-connect. I've looked this problem up, but have found no solution that works for my system/is relevant to my situation. My log files, from my latest start up, are as follows:
```
2013/02/01 10:38:02 :: ---------------------------
2013/02/01 10:38:02 :: wicd initializing...
2013/02/01 10:38:02 :: ---------------------------
2013/02/01 10:38:02 :: wicd is version 1.7.2.3 761
2013/02/01 10:38:03 :: setting backend to external
2013/02/01 10:38:03 :: trying to load backend external
2013/02/01 10:38:03 :: successfully loaded backend external
2013/02/01 10:38:03 :: trying to load backend external
2013/02/01 10:38:03 :: successfully loaded backend external
2013/02/01 10:38:03 :: Automatically detected wireless interface wlan0
2013/02/01 10:38:03 :: setting wireless interface wlan0
2013/02/01 10:38:03 :: automatically detected wired interface eth0
2013/02/01 10:38:03 :: setting wired interface eth0
2013/02/01 10:38:03 :: setting wpa driver wext
2013/02/01 10:38:03 :: setting use global dns to False
2013/02/01 10:38:03 :: setting global dns
2013/02/01 10:38:03 :: global dns servers are None None None
2013/02/01 10:38:03 :: domain is None
2013/02/01 10:38:03 :: search domain is None
2013/02/01 10:38:03 :: setting automatically reconnect when connection drops True
2013/02/01 10:38:03 :: Setting dhcp client to 0
2013/02/01 10:38:03 :: Wireless configuration file found...
2013/02/01 10:38:03 :: Wired configuration file found...
2013/02/01 10:38:03 :: chmoding configuration files 0600...
2013/02/01 10:38:03 :: chowning configuration files root:root...
2013/02/01 10:38:03 :: Using wireless interface...wlan0
2013/02/01 10:38:03 :: Using wired interface...eth0
2013/02/01 10:38:10 :: Autoconnecting...
2013/02/01 10:38:10 :: No wired connection present, attempting to autoconnect to wireless network
2013/02/01 10:38:10 :: trying to automatically connect to...Hebron
2013/02/01 10:38:10 :: Connecting to wireless network Hebron
2013/02/01 10:38:17 :: attempting to set hostname with dhclient
2013/02/01 10:38:17 :: using dhcpcd or another supported client may work better
2013/02/01 10:38:20 :: attempting to set hostname with dhclient
2013/02/01 10:38:20 :: using dhcpcd or another supported client may work better
2013/02/01 10:38:20 :: Putting interface down
2013/02/01 10:38:20 :: Releasing DHCP leases...
2013/02/01 10:38:20 :: attempting to set hostname with dhclient
2013/02/01 10:38:20 :: using dhcpcd or another supported client may work better
2013/02/01 10:38:20 :: Setting false IP...
2013/02/01 10:38:20 :: Stopping wpa_supplicant
2013/02/01 10:38:20 :: Flushing the routing table...
2013/02/01 10:38:20 :: Putting interface up...
2013/02/01 10:38:23 :: Running DHCP with hostname Aspire-5734Z
2013/02/01 10:38:23 :: attempting to set hostname with dhclient
2013/02/01 10:38:23 :: using dhcpcd or another supported client may work better
2013/02/01 10:38:23 :: Internet Systems Consortium DHCP Client 4.1-ESV-R4
2013/02/01 10:38:23 :: Copyright 2004-2011 Internet Systems Consortium.
2013/02/01 10:38:23 :: All rights reserved.
2013/02/01 10:38:23 :: For info, please visit https://www.isc.org/software/dhcp/
2013/02/01 10:38:23 :: 
2013/02/01 10:38:23 :: Listening on LPF/wlan0/78:e4:00:42:04:eb
2013/02/01 10:38:23 :: Sending on   LPF/wlan0/78:e4:00:42:04:eb
2013/02/01 10:38:23 :: Sending on   Socket/fallback
2013/02/01 10:38:23 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2013/02/01 10:38:26 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2013/02/01 10:38:34 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
2013/02/01 10:38:52 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
2013/02/01 10:39:09 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
2013/02/01 10:39:19 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
2013/02/01 10:39:34 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
2013/02/01 10:39:47 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
2013/02/01 10:40:00 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
2013/02/01 10:40:15 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
2013/02/01 10:40:35 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2013/02/01 10:40:47 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
2013/02/01 10:40:56 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
2013/02/01 10:41:12 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2013/02/01 10:41:26 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
2013/02/01 10:41:42 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
2013/02/01 10:42:02 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2013/02/01 10:42:09 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
2013/02/01 10:42:26 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2013/02/01 10:42:38 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
2013/02/01 10:42:59 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
2013/02/01 10:43:10 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2013/02/01 10:43:24 :: No DHCPOFFERS received.
2013/02/01 10:43:24 :: No working leases in persistent database - sleeping.
2013/02/01 10:43:24 :: DHCP connection failed
2013/02/01 10:43:24 :: exiting connection thread
2013/02/01 10:43:24 :: Sending connection attempt result dhcp_failed
2013/02/01 10:43:24 :: attempting to set hostname with dhclient
2013/02/01 10:43:24 :: using dhcpcd or another supported client may work better
2013/02/01 10:43:24 :: attempting to set hostname with dhclient
2013/02/01 10:43:24 :: using dhcpcd or another supported client may work better
2013/02/01 10:47:42 :: Connecting to wireless network Hebron
2013/02/01 10:47:42 :: attempting to set hostname with dhclient
2013/02/01 10:47:42 :: using dhcpcd or another supported client may work better
2013/02/01 10:47:42 :: attempting to set hostname with dhclient
2013/02/01 10:47:42 :: using dhcpcd or another supported client may work better
2013/02/01 10:47:43 :: Putting interface down
2013/02/01 10:47:43 :: Releasing DHCP leases...
2013/02/01 10:47:43 :: attempting to set hostname with dhclient
2013/02/01 10:47:43 :: using dhcpcd or another supported client may work better
2013/02/01 10:47:43 :: Setting false IP...
2013/02/01 10:47:43 :: Stopping wpa_supplicant
2013/02/01 10:47:43 :: Flushing the routing table...
2013/02/01 10:47:43 :: Putting interface up...
2013/02/01 10:47:45 :: Running DHCP with hostname Aspire-5734Z
2013/02/01 10:47:45 :: attempting to set hostname with dhclient
2013/02/01 10:47:45 :: using dhcpcd or another supported client may work better
2013/02/01 10:47:45 :: Internet Systems Consortium DHCP Client 4.1-ESV-R4
2013/02/01 10:47:45 :: Copyright 2004-2011 Internet Systems Consortium.
2013/02/01 10:47:45 :: All rights reserved.
2013/02/01 10:47:45 :: For info, please visit https://www.isc.org/software/dhcp/
2013/02/01 10:47:45 :: 
2013/02/01 10:47:45 :: Listening on LPF/wlan0/78:e4:00:42:04:eb
2013/02/01 10:47:45 :: Sending on   LPF/wlan0/78:e4:00:42:04:eb
2013/02/01 10:47:45 :: Sending on   Socket/fallback
2013/02/01 10:47:45 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2013/02/01 10:47:46 :: DHCPREQUEST of 10.10.239.246 on wlan0 to 255.255.255.255 port 67
2013/02/01 10:47:46 :: DHCPOFFER of 10.10.239.246 from 10.10.1.1
2013/02/01 10:47:46 :: DHCPACK of 10.10.239.246 from 10.10.1.1
2013/02/01 10:47:46 :: bound to 10.10.239.246 -- renewal in 12738894 seconds.
2013/02/01 10:47:46 :: DHCP connection successful
2013/02/01 10:47:46 :: not verifying
2013/02/01 10:47:46 :: Connecting thread exiting.
2013/02/01 10:47:46 :: Sending connection attempt result success
```
It is important to note that when I tell it to refresh networks myself and when I tell it to connect to a given network myself, it works flawlessly. I'd just like for it to happen automatically so that it's less of a pain, and my weather app (this is crucial :D) displays info without having to restart E17. I am running Bodhi by the way, which is based on Ubuntu. Any help will be much appreciated!

---

