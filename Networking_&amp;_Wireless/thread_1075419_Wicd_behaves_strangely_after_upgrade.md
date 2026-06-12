---
title: "Wicd behaves strangely after upgrade"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2009-02-20
Hi All

After a recent upgrade of the Wicd package to v 1.5.9, I am observing something odd.  When I boot, Wicd starts fine, but does not connect to my preferred network as before.  I can open up the GUI and manipulate that absolutely fine, but if I click 'connect' on my network, it doesn't.

I have tried disconnect, refresh and re-connect; all to no avail.  The only way I can get Wicd to work properly is by (after boot) turn my wireless router off and on again.

I have a vague recollection of something similar happening last time I upgraded, by can't for the life of me remember how I solved it!

Here's /var/log/wicd , showing today's activity.

```
2009/02/20 10:16:14 :: ---------------------------
2009/02/20 10:16:14 :: wicd initializing...
2009/02/20 10:16:14 :: ---------------------------
2009/02/20 10:16:14 :: Automatically detected wireless interface wlan0
2009/02/20 10:16:14 :: found wireless_interface in configuration wlan0
2009/02/20 10:16:14 :: setting wireless interface wlan0
2009/02/20 10:16:14 :: automatically detected wired interface eth0
2009/02/20 10:16:14 :: found wired_interface in configuration eth0
2009/02/20 10:16:14 :: setting wired interface eth0
2009/02/20 10:16:14 :: found wpa_driver in configuration wext
2009/02/20 10:16:14 :: setting wpa driver wext
2009/02/20 10:16:14 :: found always_show_wired_interface in configuration False
2009/02/20 10:16:14 :: found use_global_dns in configuration False
2009/02/20 10:16:14 :: setting use global dns to False
2009/02/20 10:16:14 :: setting use global dns to boolean False
2009/02/20 10:16:14 :: found global_dns_1 in configuration None
2009/02/20 10:16:14 :: found global_dns_2 in configuration None
2009/02/20 10:16:14 :: found global_dns_3 in configuration None
2009/02/20 10:16:14 :: setting global dns
2009/02/20 10:16:14 :: global dns servers are None None None
2009/02/20 10:16:14 :: found auto_reconnect in configuration True
2009/02/20 10:16:14 :: setting automatically reconnect when connection drops
2009/02/20 10:16:14 :: found debug_mode in configuration 0
2009/02/20 10:16:14 :: found wired_connect_mode in configuration 1
2009/02/20 10:16:14 :: found signal_display_type in configuration 0
2009/02/20 10:16:14 :: found dhcp_client in configuration 0
2009/02/20 10:16:14 :: Setting dhcp client to 0
2009/02/20 10:16:14 :: found link_detect_tool in configuration 0
2009/02/20 10:16:14 :: found flush_tool in configuration 0
2009/02/20 10:16:14 :: Wireless configuration file found...
2009/02/20 10:16:14 :: Wired configuration file found...
2009/02/20 10:16:14 :: chmoding configuration files 0600...
2009/02/20 10:16:14 :: chowning configuration files root:root...
2009/02/20 10:16:14 :: Using wired interface...eth0
2009/02/20 10:16:14 :: Using wireless interface...wlan0
2009/02/20 10:16:15 :: autoconnecting... wlan0
2009/02/20 10:16:20 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 10:16:20 :: trying to automatically connect to...CharlesNet
2009/02/20 10:16:20 :: Connecting to wireless network CharlesNet
2009/02/20 10:16:20 :: Putting interface down
2009/02/20 10:16:20 :: Releasing DHCP leases...
2009/02/20 10:16:21 :: Setting false IP...
2009/02/20 10:16:22 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:16:22 :: Flushing the routing table...
2009/02/20 10:16:22 :: Generating psk...
2009/02/20 10:16:22 :: Attempting to authenticate...
2009/02/20 10:16:23 :: Putting interface up...
2009/02/20 10:16:28 :: Running DHCP
2009/02/20 10:16:28 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:16:28 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:16:28 :: All rights reserved.
2009/02/20 10:16:28 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:16:28 :: 
2009/02/20 10:16:28 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:30 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:30 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:30 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:30 :: Sending on   Socket/fallback
2009/02/20 10:16:33 :: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:16:33 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:16:33 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:16:33 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:16:33 :: SIOCADDRT: No such process
2009/02/20 10:16:33 :: bound to 0.0.0.0 -- renewal in 40608 seconds.
2009/02/20 10:16:33 :: DHCP connection successful
2009/02/20 10:16:33 :: Connecting thread exiting.
2009/02/20 10:16:38 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 10:16:38 :: trying to automatically connect to...CharlesNet
2009/02/20 10:16:38 :: Connecting to wireless network CharlesNet
2009/02/20 10:16:38 :: Putting interface down
2009/02/20 10:16:38 :: Releasing DHCP leases...
2009/02/20 10:16:38 :: Setting false IP...
2009/02/20 10:16:38 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:16:38 :: Flushing the routing table...
2009/02/20 10:16:38 :: Generating psk...
2009/02/20 10:16:38 :: Attempting to authenticate...
2009/02/20 10:16:38 :: Putting interface up...
2009/02/20 10:16:44 :: Running DHCP
2009/02/20 10:16:44 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:16:44 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:16:44 :: All rights reserved.
2009/02/20 10:16:44 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:16:44 :: 
2009/02/20 10:16:44 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:45 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:45 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:45 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:45 :: Sending on   Socket/fallback
2009/02/20 10:16:47 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:16:47 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:16:47 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:16:47 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:16:47 :: SIOCADDRT: No such process
2009/02/20 10:16:47 :: bound to 0.0.0.0 -- renewal in 43168 seconds.
2009/02/20 10:16:47 :: DHCP connection successful
2009/02/20 10:16:47 :: Connecting thread exiting.
2009/02/20 10:16:52 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 10:16:52 :: trying to automatically connect to...CharlesNet
2009/02/20 10:16:52 :: Connecting to wireless network CharlesNet
2009/02/20 10:16:52 :: Putting interface down
2009/02/20 10:16:52 :: Releasing DHCP leases...
2009/02/20 10:16:52 :: Setting false IP...
2009/02/20 10:16:52 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:16:52 :: Flushing the routing table...
2009/02/20 10:16:52 :: Generating psk...
2009/02/20 10:16:52 :: Attempting to authenticate...
2009/02/20 10:16:52 :: Putting interface up...
2009/02/20 10:16:53 :: Running DHCP
2009/02/20 10:16:53 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:16:53 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:16:53 :: All rights reserved.
2009/02/20 10:16:53 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:16:53 :: 
2009/02/20 10:16:53 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:54 :: wmaster0: unknown hardware address type 801
2009/02/20 10:16:54 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:54 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:16:54 :: Sending on   Socket/fallback
2009/02/20 10:16:55 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:16:55 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:16:55 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:16:55 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:16:55 :: SIOCADDRT: No such process
2009/02/20 10:16:55 :: bound to 0.0.0.0 -- renewal in 35412 seconds.
2009/02/20 10:16:55 :: DHCP connection successful
2009/02/20 10:16:55 :: Connecting thread exiting.
2009/02/20 10:17:01 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 10:17:01 :: trying to automatically connect to...CharlesNet
2009/02/20 10:17:01 :: Connecting to wireless network CharlesNet
2009/02/20 10:17:01 :: Putting interface down
2009/02/20 10:17:01 :: Releasing DHCP leases...
2009/02/20 10:17:01 :: Setting false IP...
2009/02/20 10:17:01 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:17:01 :: Flushing the routing table...
2009/02/20 10:17:01 :: Generating psk...
2009/02/20 10:17:01 :: Attempting to authenticate...
2009/02/20 10:17:02 :: Putting interface up...
2009/02/20 10:17:07 :: Running DHCP
2009/02/20 10:17:07 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:17:07 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:17:07 :: All rights reserved.
2009/02/20 10:17:07 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:17:07 :: 
2009/02/20 10:17:07 :: wmaster0: unknown hardware address type 801
2009/02/20 10:17:08 :: wmaster0: unknown hardware address type 801
2009/02/20 10:17:08 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:17:08 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:17:08 :: Sending on   Socket/fallback
2009/02/20 10:17:09 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:17:09 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:17:09 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:17:09 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:17:09 :: SIOCADDRT: No such process
2009/02/20 10:17:09 :: bound to 0.0.0.0 -- renewal in 39936 seconds.
2009/02/20 10:17:09 :: DHCP connection successful
2009/02/20 10:17:09 :: Connecting thread exiting.
2009/02/20 10:18:24 :: Connecting to wireless network CharlesNet
2009/02/20 10:18:24 :: Putting interface down
2009/02/20 10:18:24 :: Releasing DHCP leases...
2009/02/20 10:18:25 :: Setting false IP...
2009/02/20 10:18:25 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:18:25 :: Flushing the routing table...
2009/02/20 10:18:25 :: Generating psk...
2009/02/20 10:18:25 :: Attempting to authenticate...
2009/02/20 10:18:26 :: Putting interface up...
2009/02/20 10:18:31 :: Running DHCP
2009/02/20 10:18:31 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:18:31 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:18:31 :: All rights reserved.
2009/02/20 10:18:31 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:18:31 :: 
2009/02/20 10:18:31 :: wmaster0: unknown hardware address type 801
2009/02/20 10:18:32 :: wmaster0: unknown hardware address type 801
2009/02/20 10:18:32 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:18:32 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:18:32 :: Sending on   Socket/fallback
2009/02/20 10:18:34 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:18:34 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:18:34 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:18:34 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:18:34 :: SIOCADDRT: No such process
2009/02/20 10:18:34 :: bound to 0.0.0.0 -- renewal in 33928 seconds.
2009/02/20 10:18:34 :: DHCP connection successful
2009/02/20 10:18:34 :: Connecting thread exiting.
2009/02/20 10:18:58 :: Connecting to wireless network CharlesNet
2009/02/20 10:18:58 :: Putting interface down
2009/02/20 10:18:58 :: Releasing DHCP leases...
2009/02/20 10:18:59 :: Setting false IP...
2009/02/20 10:18:59 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:18:59 :: Flushing the routing table...
2009/02/20 10:18:59 :: Generating psk...
2009/02/20 10:18:59 :: Attempting to authenticate...
2009/02/20 10:19:00 :: Putting interface up...
2009/02/20 10:19:05 :: Running DHCP
2009/02/20 10:19:05 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:19:05 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:19:05 :: All rights reserved.
2009/02/20 10:19:05 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:19:05 :: 
2009/02/20 10:19:05 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:06 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:06 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:06 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:06 :: Sending on   Socket/fallback
2009/02/20 10:19:09 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:19:09 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:19:09 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:19:09 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:19:09 :: SIOCADDRT: No such process
2009/02/20 10:19:09 :: bound to 0.0.0.0 -- renewal in 38608 seconds.
2009/02/20 10:19:09 :: DHCP connection successful
2009/02/20 10:19:09 :: Connecting thread exiting.
2009/02/20 10:19:11 :: Connecting to wireless network CharlesNet
2009/02/20 10:19:11 :: Putting interface down
2009/02/20 10:19:11 :: Releasing DHCP leases...
2009/02/20 10:19:11 :: Setting false IP...
2009/02/20 10:19:11 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:19:11 :: Flushing the routing table...
2009/02/20 10:19:11 :: Generating psk...
2009/02/20 10:19:11 :: Attempting to authenticate...
2009/02/20 10:19:12 :: Putting interface up...
2009/02/20 10:19:18 :: Running DHCP
2009/02/20 10:19:18 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:19:18 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:19:18 :: All rights reserved.
2009/02/20 10:19:18 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:19:18 :: 
2009/02/20 10:19:18 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:19 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:19 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:19 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:19 :: Sending on   Socket/fallback
2009/02/20 10:19:21 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:19:21 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:19:21 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:19:21 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:19:21 :: SIOCADDRT: No such process
2009/02/20 10:19:21 :: bound to 0.0.0.0 -- renewal in 34690 seconds.
2009/02/20 10:19:21 :: DHCP connection successful
2009/02/20 10:19:21 :: Connecting thread exiting.
2009/02/20 10:19:32 :: Connecting to wireless network CharlesNet
2009/02/20 10:19:32 :: Putting interface down
2009/02/20 10:19:32 :: Releasing DHCP leases...
2009/02/20 10:19:33 :: Setting false IP...
2009/02/20 10:19:33 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:19:33 :: Flushing the routing table...
2009/02/20 10:19:33 :: Generating psk...
2009/02/20 10:19:33 :: Attempting to authenticate...
2009/02/20 10:19:34 :: Putting interface up...
2009/02/20 10:19:35 :: Running DHCP
2009/02/20 10:19:35 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:19:35 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:19:35 :: All rights reserved.
2009/02/20 10:19:35 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:19:35 :: 
2009/02/20 10:19:35 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:36 :: wmaster0: unknown hardware address type 801
2009/02/20 10:19:36 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:36 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:19:36 :: Sending on   Socket/fallback
2009/02/20 10:19:40 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:19:40 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:19:40 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:19:40 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:19:40 :: SIOCADDRT: No such process
2009/02/20 10:19:40 :: bound to 0.0.0.0 -- renewal in 37549 seconds.
2009/02/20 10:19:40 :: DHCP connection successful
2009/02/20 10:19:40 :: Connecting thread exiting.
2009/02/20 10:19:55 :: Connecting to wireless network CharlesNet
2009/02/20 10:19:55 :: Putting interface down
2009/02/20 10:19:55 :: Releasing DHCP leases...
2009/02/20 10:19:55 :: Setting false IP...
2009/02/20 10:19:55 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:19:55 :: Flushing the routing table...
2009/02/20 10:19:55 :: Generating psk...
2009/02/20 10:19:55 :: Attempting to authenticate...
2009/02/20 10:19:56 :: Putting interface up...
2009/02/20 10:20:02 :: Running DHCP
2009/02/20 10:20:02 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:20:02 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:20:02 :: All rights reserved.
2009/02/20 10:20:02 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:20:02 :: 
2009/02/20 10:20:02 :: wmaster0: unknown hardware address type 801
2009/02/20 10:20:03 :: wmaster0: unknown hardware address type 801
2009/02/20 10:20:03 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:20:03 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:20:03 :: Sending on   Socket/fallback
2009/02/20 10:20:05 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:20:05 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:20:05 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:20:05 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:20:05 :: SIOCADDRT: No such process
2009/02/20 10:20:05 :: bound to 0.0.0.0 -- renewal in 41017 seconds.
2009/02/20 10:20:05 :: DHCP connection successful
2009/02/20 10:20:05 :: Connecting thread exiting.
2009/02/20 10:20:41 :: Connecting to wireless network CharlesNet
2009/02/20 10:20:41 :: Putting interface down
2009/02/20 10:20:41 :: Releasing DHCP leases...
2009/02/20 10:20:41 :: Setting false IP...
2009/02/20 10:20:41 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:20:42 :: Flushing the routing table...
2009/02/20 10:20:42 :: Generating psk...
2009/02/20 10:20:42 :: Attempting to authenticate...
2009/02/20 10:20:43 :: Putting interface up...
2009/02/20 10:20:48 :: Running DHCP
2009/02/20 10:20:48 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:20:48 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:20:48 :: All rights reserved.
2009/02/20 10:20:48 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:20:48 :: 
2009/02/20 10:20:48 :: wmaster0: unknown hardware address type 801
2009/02/20 10:20:49 :: wmaster0: unknown hardware address type 801
2009/02/20 10:20:49 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:20:49 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:20:49 :: Sending on   Socket/fallback
2009/02/20 10:20:51 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:20:51 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:20:51 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:20:51 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:20:51 :: SIOCADDRT: No such process
2009/02/20 10:20:51 :: bound to 0.0.0.0 -- renewal in 39961 seconds.
2009/02/20 10:20:51 :: DHCP connection successful
2009/02/20 10:20:51 :: Connecting thread exiting.
2009/02/20 10:21:12 :: Connecting to wireless network CharlesNet
2009/02/20 10:21:12 :: Putting interface down
2009/02/20 10:21:12 :: Releasing DHCP leases...
2009/02/20 10:21:12 :: Setting false IP...
2009/02/20 10:21:12 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:21:12 :: Flushing the routing table...
2009/02/20 10:21:13 :: Generating psk...
2009/02/20 10:21:13 :: Attempting to authenticate...
2009/02/20 10:21:14 :: Putting interface up...
2009/02/20 10:21:19 :: Running DHCP
2009/02/20 10:21:19 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:21:19 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:21:19 :: All rights reserved.
2009/02/20 10:21:19 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:21:19 :: 
2009/02/20 10:21:19 :: wmaster0: unknown hardware address type 801
2009/02/20 10:21:20 :: wmaster0: unknown hardware address type 801
2009/02/20 10:21:20 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:21:20 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:21:20 :: Sending on   Socket/fallback
2009/02/20 10:21:22 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:21:22 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:21:22 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:21:22 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:21:22 :: SIOCADDRT: No such process
2009/02/20 10:21:22 :: bound to 0.0.0.0 -- renewal in 42640 seconds.
2009/02/20 10:21:22 :: DHCP connection successful
2009/02/20 10:21:22 :: Connecting thread exiting.
2009/02/20 10:21:44 :: Connecting to wireless network CharlesNet
2009/02/20 10:21:44 :: Putting interface down
2009/02/20 10:21:44 :: Releasing DHCP leases...
2009/02/20 10:21:44 :: Setting false IP...
2009/02/20 10:21:44 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:21:44 :: Flushing the routing table...
2009/02/20 10:21:45 :: Generating psk...
2009/02/20 10:21:45 :: Attempting to authenticate...
2009/02/20 10:21:46 :: Putting interface up...
2009/02/20 10:21:51 :: Running DHCP
2009/02/20 10:21:51 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:21:51 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:21:51 :: All rights reserved.
2009/02/20 10:21:51 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:21:51 :: 
2009/02/20 10:21:51 :: wmaster0: unknown hardware address type 801
2009/02/20 10:21:52 :: wmaster0: unknown hardware address type 801
2009/02/20 10:21:52 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:21:52 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:21:52 :: Sending on   Socket/fallback
2009/02/20 10:21:55 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:21:55 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:21:55 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:21:55 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:21:55 :: SIOCADDRT: No such process
2009/02/20 10:21:55 :: bound to 0.0.0.0 -- renewal in 39743 seconds.
2009/02/20 10:21:55 :: DHCP connection successful
2009/02/20 10:21:55 :: Connecting thread exiting.
2009/02/20 10:22:02 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 10:22:02 :: trying to automatically connect to...CharlesNet
2009/02/20 10:22:02 :: Connecting to wireless network CharlesNet
2009/02/20 10:22:02 :: Putting interface down
2009/02/20 10:22:02 :: Releasing DHCP leases...
2009/02/20 10:22:02 :: Setting false IP...
2009/02/20 10:22:02 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:22:02 :: Flushing the routing table...
2009/02/20 10:22:02 :: Generating psk...
2009/02/20 10:22:02 :: Attempting to authenticate...
2009/02/20 10:22:04 :: Putting interface up...
2009/02/20 10:22:09 :: Running DHCP
2009/02/20 10:22:09 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:22:09 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:22:09 :: All rights reserved.
2009/02/20 10:22:09 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:22:09 :: 
2009/02/20 10:22:09 :: wmaster0: unknown hardware address type 801
2009/02/20 10:22:10 :: wmaster0: unknown hardware address type 801
2009/02/20 10:22:10 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:22:10 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:22:10 :: Sending on   Socket/fallback
2009/02/20 10:22:10 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:22:13 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:22:20 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:22:27 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2009/02/20 10:22:30 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2009/02/20 10:22:38 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2009/02/20 10:22:52 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
2009/02/20 10:23:04 :: canceling connection attempt
2009/02/20 10:23:04 :: DHCP connection failed
2009/02/20 10:23:04 :: exiting connection thread
2009/02/20 10:23:08 :: Connecting to wireless network CharlesNet
2009/02/20 10:23:08 :: Putting interface down
2009/02/20 10:23:08 :: Releasing DHCP leases...
2009/02/20 10:23:08 :: Setting false IP...
2009/02/20 10:23:08 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 10:23:09 :: Flushing the routing table...
2009/02/20 10:23:09 :: Generating psk...
2009/02/20 10:23:09 :: Attempting to authenticate...
2009/02/20 10:23:09 :: Putting interface up...
2009/02/20 10:23:14 :: Running DHCP
2009/02/20 10:23:14 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 10:23:14 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 10:23:14 :: All rights reserved.
2009/02/20 10:23:14 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 10:23:14 :: 
2009/02/20 10:23:14 :: wmaster0: unknown hardware address type 801
2009/02/20 10:23:15 :: wmaster0: unknown hardware address type 801
2009/02/20 10:23:15 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:23:15 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 10:23:15 :: Sending on   Socket/fallback
2009/02/20 10:23:15 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:23:15 :: DHCPNAK from 192.168.1.1
2009/02/20 10:23:26 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2009/02/20 10:23:28 :: DHCPOFFER of 192.168.1.2 from 192.168.1.1
2009/02/20 10:23:28 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:23:31 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:23:31 :: DHCPACK of 192.168.1.2 from 192.168.1.1
2009/02/20 10:23:31 :: bound to 192.168.1.2 -- renewal in 39523 seconds.
2009/02/20 10:23:31 :: DHCP connection successful
2009/02/20 10:23:31 :: Connecting thread exiting.
2009/02/20 13:44:54 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 13:44:54 :: trying to automatically connect to...CharlesNet
2009/02/20 13:44:54 :: Connecting to wireless network CharlesNet
2009/02/20 13:44:54 :: Putting interface down
2009/02/20 13:44:54 :: Releasing DHCP leases...
2009/02/20 13:44:55 :: Setting false IP...
2009/02/20 13:44:55 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:44:55 :: Flushing the routing table...
2009/02/20 13:44:55 :: Generating psk...
2009/02/20 13:44:55 :: Attempting to authenticate...
2009/02/20 13:44:56 :: Putting interface up...
2009/02/20 13:44:57 :: Running DHCP
2009/02/20 13:44:57 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 13:44:57 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 13:44:57 :: All rights reserved.
2009/02/20 13:44:57 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 13:44:57 :: 
2009/02/20 13:44:57 :: wmaster0: unknown hardware address type 801
2009/02/20 13:44:58 :: wmaster0: unknown hardware address type 801
2009/02/20 13:44:58 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:44:58 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:44:58 :: Sending on   Socket/fallback
2009/02/20 13:44:58 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:44:58 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 13:44:59 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 13:44:59 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 13:44:59 :: SIOCADDRT: No such process
2009/02/20 13:44:59 :: bound to 0.0.0.0 -- renewal in 40000 seconds.
2009/02/20 13:44:59 :: DHCP connection successful
2009/02/20 13:44:59 :: Connecting thread exiting.
2009/02/20 13:45:05 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 13:45:05 :: trying to automatically connect to...CharlesNet
2009/02/20 13:45:05 :: Connecting to wireless network CharlesNet
2009/02/20 13:45:05 :: Putting interface down
2009/02/20 13:45:05 :: Releasing DHCP leases...
2009/02/20 13:45:05 :: Setting false IP...
2009/02/20 13:45:05 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:45:05 :: Flushing the routing table...
2009/02/20 13:45:05 :: Generating psk...
2009/02/20 13:45:05 :: Attempting to authenticate...
2009/02/20 13:45:05 :: Putting interface up...
2009/02/20 13:45:46 :: wpa_supplicant authentication may have failed.
2009/02/20 13:45:46 :: exiting connection thread
2009/02/20 13:45:49 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 13:45:49 :: trying to automatically connect to...CharlesNet
2009/02/20 13:45:49 :: Connecting to wireless network CharlesNet
2009/02/20 13:45:49 :: Putting interface down
2009/02/20 13:45:49 :: Releasing DHCP leases...
2009/02/20 13:45:50 :: Setting false IP...
2009/02/20 13:45:50 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:45:50 :: Flushing the routing table...
2009/02/20 13:45:50 :: Generating psk...
2009/02/20 13:45:50 :: Attempting to authenticate...
2009/02/20 13:45:51 :: Putting interface up...
2009/02/20 13:45:57 :: Running DHCP
2009/02/20 13:45:57 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 13:45:57 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 13:45:57 :: All rights reserved.
2009/02/20 13:45:57 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 13:45:57 :: 
2009/02/20 13:45:57 :: wmaster0: unknown hardware address type 801
2009/02/20 13:45:58 :: wmaster0: unknown hardware address type 801
2009/02/20 13:45:58 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:45:58 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:45:58 :: Sending on   Socket/fallback
2009/02/20 13:46:02 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:46:02 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 13:46:02 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 13:46:02 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 13:46:02 :: SIOCADDRT: No such process
2009/02/20 13:46:02 :: bound to 0.0.0.0 -- renewal in 42933 seconds.
2009/02/20 13:46:02 :: DHCP connection successful
2009/02/20 13:46:02 :: Connecting thread exiting.
2009/02/20 13:46:07 :: No wired connection present, attempting to autoconnect to wireless network
2009/02/20 13:46:07 :: trying to automatically connect to...CharlesNet
2009/02/20 13:46:07 :: Connecting to wireless network CharlesNet
2009/02/20 13:46:07 :: Putting interface down
2009/02/20 13:46:07 :: Releasing DHCP leases...
2009/02/20 13:46:07 :: Setting false IP...
2009/02/20 13:46:07 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:46:07 :: Flushing the routing table...
2009/02/20 13:46:07 :: Generating psk...
2009/02/20 13:46:07 :: Attempting to authenticate...
2009/02/20 13:46:07 :: Putting interface up...
2009/02/20 13:46:12 :: Running DHCP
2009/02/20 13:46:12 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 13:46:12 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 13:46:12 :: All rights reserved.
2009/02/20 13:46:12 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 13:46:12 :: 
2009/02/20 13:46:12 :: wmaster0: unknown hardware address type 801
2009/02/20 13:46:13 :: wmaster0: unknown hardware address type 801
2009/02/20 13:46:13 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:46:13 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:46:13 :: Sending on   Socket/fallback
2009/02/20 13:46:13 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:46:13 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 13:46:13 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 13:46:13 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 13:46:13 :: SIOCADDRT: No such process
2009/02/20 13:46:13 :: bound to 0.0.0.0 -- renewal in 36885 seconds.
2009/02/20 13:46:13 :: DHCP connection successful
2009/02/20 13:46:13 :: Connecting thread exiting.
2009/02/20 13:48:00 :: Connecting to wireless network CharlesNet
2009/02/20 13:48:00 :: Putting interface down
2009/02/20 13:48:00 :: Releasing DHCP leases...
2009/02/20 13:48:01 :: Setting false IP...
2009/02/20 13:48:01 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:48:01 :: Flushing the routing table...
2009/02/20 13:48:01 :: Generating psk...
2009/02/20 13:48:01 :: Attempting to authenticate...
2009/02/20 13:48:02 :: Putting interface up...
2009/02/20 13:48:07 :: Running DHCP
2009/02/20 13:48:07 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 13:48:07 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 13:48:07 :: All rights reserved.
2009/02/20 13:48:07 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 13:48:07 :: 
2009/02/20 13:48:07 :: wmaster0: unknown hardware address type 801
2009/02/20 13:48:08 :: wmaster0: unknown hardware address type 801
2009/02/20 13:48:08 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:48:08 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:48:08 :: Sending on   Socket/fallback
2009/02/20 13:48:08 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:48:08 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 13:48:08 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 13:48:08 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 13:48:08 :: SIOCADDRT: No such process
2009/02/20 13:48:08 :: bound to 0.0.0.0 -- renewal in 35575 seconds.
2009/02/20 13:48:08 :: DHCP connection successful
2009/02/20 13:48:08 :: Connecting thread exiting.
2009/02/20 13:48:24 :: setting use global dns to 0
2009/02/20 13:48:24 :: setting use global dns to boolean False
2009/02/20 13:48:24 :: setting global dns
2009/02/20 13:48:24 :: global dns servers are   
2009/02/20 13:48:24 :: setting wireless interface wlan0
2009/02/20 13:48:24 :: setting wired interface eth0
2009/02/20 13:48:24 :: setting wpa driver wext
2009/02/20 13:48:24 :: setting automatically reconnect when connection drops
2009/02/20 13:48:24 :: Setting dhcp client to 0
2009/02/20 13:50:12 :: Connecting to wireless network CharlesNet
2009/02/20 13:50:12 :: Putting interface down
2009/02/20 13:50:13 :: Releasing DHCP leases...
2009/02/20 13:50:13 :: Setting false IP...
2009/02/20 13:50:13 :: Stopping wpa_supplicant and any DHCP clients
2009/02/20 13:50:13 :: Flushing the routing table...
2009/02/20 13:50:13 :: Generating psk...
2009/02/20 13:50:13 :: Attempting to authenticate...
2009/02/20 13:50:14 :: Putting interface up...
2009/02/20 13:50:20 :: Running DHCP
2009/02/20 13:50:20 :: Internet Systems Consortium DHCP Client V3.1.1
2009/02/20 13:50:20 :: Copyright 2004-2008 Internet Systems Consortium.
2009/02/20 13:50:20 :: All rights reserved.
2009/02/20 13:50:20 :: For info, please visit http://www.isc.org/sw/dhcp/
2009/02/20 13:50:20 :: 
2009/02/20 13:50:20 :: wmaster0: unknown hardware address type 801
2009/02/20 13:50:21 :: wmaster0: unknown hardware address type 801
2009/02/20 13:50:21 :: Listening on LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:50:21 :: Sending on   LPF/wlan0/00:1c:bf:69:1e:97
2009/02/20 13:50:21 :: Sending on   Socket/fallback
2009/02/20 13:50:22 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:22 :: DHCPNAK from 192.168.1.1
2009/02/20 13:50:32 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2009/02/20 13:50:34 :: DHCPOFFER of 192.168.1.2 from 192.168.1.1
2009/02/20 13:50:34 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:42 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:42 :: DHCPACK of 192.168.1.2 from 192.168.1.1
2009/02/20 13:50:42 :: bound to 192.168.1.2 -- renewal in 39341 seconds.
2009/02/20 13:50:42 :: DHCP connection successful
2009/02/20 13:50:42 :: Connecting thread exiting.
```

All help appreciated.

Charlie

Ubuntu 8.10

---

### Post by imdano on 2009-02-20
```
2009/02/20 10:21:55 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 10:21:55 :: DHCPACK of 0.0.0.0 from 192.168.1.1
2009/02/20 10:21:55 :: SIOCSIFNETMASK: Cannot assign requested address
2009/02/20 10:21:55 :: SIOCSIFBRDADDR: Cannot assign requested address
2009/02/20 10:21:55 :: SIOCADDRT: No such process
2009/02/20 10:21:55 :: bound to 0.0.0.0 -- renewal in 39743 seconds.
```For some reason your route is ACKing a DHCP request on 0.0.0.0.  When your connection succeeds, it NACKs it, which is what it should be doing, I would think ```
2009/02/20 13:50:22 :: DHCPREQUEST of 0.0.0.0 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:22 :: DHCPNAK from 192.168.1.1
2009/02/20 13:50:32 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2009/02/20 13:50:34 :: DHCPOFFER of 192.168.1.2 from 192.168.1.1
2009/02/20 13:50:34 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:42 :: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
2009/02/20 13:50:42 :: DHCPACK of 192.168.1.2 from 192.168.1.1
2009/02/20 13:50:42 :: bound to 192.168.1.2 -- renewal in 39341 seconds.

```Unfortunately, I can't tell you why it's happening or how to fix it...

---

### Post by FokkerCharlie on 2009-02-20
Hmmm.

OK, I think that it could be something to do with the static IP that I have set up with my WLAN here.  I have re-installed via Synaptic, and that might have cured the problem.

Cheers
Charlie

---

