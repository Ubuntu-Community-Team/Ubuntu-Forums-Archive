---
title: "Network connection getting lost"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by niranjan_rao on 2009-11-23
Folks,

I upgraded from 8.* ( don't remember the exact version number) to latest 9 release available for download. Sorry for the verbose message, just trying to provide as much information as I can.

After upgrading I am loosing the network connectivity after around 5 minutes of uptime. When I boot the system, I am connected to network and somewhere down the line it lost the connection. I really don't know after how much time it looses the connection but it does happen.

Only thing I was doing when this happened was 
1. Browsing using firefox while system updated the patches
2. Trying  the games installed locally on the system while system updated the patches.

In both the cases, updater complained after few minutes that network connectivity is lost.

Other devices in my home - wired and wireless do continue to work properly. My router does not show Ubuntu as connected machine WHEN the network goes down.

This is NOT a wireless card and never had this problem with earlier version of Ubuntu.

I tried checking the logs and (if memory serves right as I am not in front of the machine now) it mentions something about DHCP and failed because of reason 5 whatever that is.

I don't know if it's related problem or cause of the problem, but I noticed similar thing while installation. Installer was stuck at installing "apt" for almost 20 minutes before I decided to hit the skip button. Same thing happened for language pack installation also.

Any help is greatly appreciated.

---

### Post by niranjan_rao on 2009-11-23
Here is the log of events for my network problem

Nov 23 20:47:03 ubuntu1 NetworkManager: <info>  (eth0): device state change: 8 -> 3 (reason 39)
Nov 23 20:47:03 ubuntu1 NetworkManager: <info>  (eth0): deactivating device (reason: 39).
Nov 23 20:47:03 ubuntu1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 979
Nov 23 20:47:03 ubuntu1 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Nov 23 20:47:03 ubuntu1 avahi-daemon[771]: Withdrawing address record for 192.168.1.6 on eth0.
Nov 23 20:47:03 ubuntu1 avahi-daemon[771]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.6.
Nov 23 20:47:03 ubuntu1 avahi-daemon[771]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  dhclient started with pid 2627
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 23 20:47:09 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 23 20:47:10 ubuntu1 dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov 23 20:47:10 ubuntu1 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 23 20:47:10 ubuntu1 dhclient: All rights reserved.
Nov 23 20:47:10 ubuntu1 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 23 20:47:10 ubuntu1 dhclient: 
Nov 23 20:47:10 ubuntu1 dhclient: Listening on LPF/eth0/00:a0:cc:db:ba:25
Nov 23 20:47:10 ubuntu1 dhclient: Sending on   LPF/eth0/00:a0:cc:db:ba:25
Nov 23 20:47:10 ubuntu1 dhclient: Sending on   Socket/fallback
Nov 23 20:47:10 ubuntu1 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Nov 23 20:47:13 ubuntu1 dhclient: DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
Nov 23 20:47:17 ubuntu1 dhclient: DHCPREQUEST of 192.168.1.6 on eth0 to 255.255.255.255 port 67
Nov 23 20:47:28 ubuntu1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 23 20:47:35 ubuntu1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 23 20:47:45 ubuntu1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2627
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  Activation (eth0) failed.
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Nov 23 20:47:55 ubuntu1 NetworkManager: <info>  (eth0): deactivating device (reason: 0).

---

### Post by SabreWolfy on 2009-12-14
IIRC, I had a similar error under Hardy/Jaunty on my wired desktop machine. I've switched to using WICD instead of Network Manager since then and it works fine. Using Karmic on the machine now.

My Karmic (previously Jaunty) server loses it's connection to my router every few days; dhclient keeps sending dhcprequests but the machine is dead on the network.

---

