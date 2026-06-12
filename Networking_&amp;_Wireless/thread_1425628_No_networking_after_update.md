---
title: "No networking after update"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by gabello on 2010-03-09
Hi,

I've just updated my ubuntu machine after a longer period of time of not using it and after the restart I'm not able to connect to any wifi or wired connection (that were working before). When I click on any network the red point starts moving around as the system is trying to get the IP from DHCP but it stays like this forever. In syslog I have: 


Update: Seems that my problem is from DHCP as I'm able to connect if I configure the IP, Mask etc manually. But I still don't know how to solve this.

---

### Post by gabello on 2010-03-09
Here is the syslog for DHCP:

```
Mar  9 19:21:27 my-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> associated
Mar  9 19:21:27 my-laptop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> completed
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'.
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Mar  9 19:21:27 my-laptop NetworkManager: <info>  (wlan1): device state change: 5 -> 7 (reason 0)
Mar  9 19:21:27 my-laptop NetworkManager: Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar  9 19:21:27 my-laptop NetworkManager: <info>  dhclient started with pid 3109
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Mar  9 19:21:27 my-laptop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Mar  9 19:21:27 my-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar  9 19:21:27 my-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar  9 19:21:27 my-laptop dhclient: All rights reserved.
Mar  9 19:21:27 my-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar  9 19:21:27 my-laptop dhclient: Usage: dhclient [-1dqrx] [-nw] [-p <port>] [-s server]
Mar  9 19:21:27 my-laptop dhclient:                 [-cf config-file] [-lf lease-file][-pf pid-file] [-e VAR=val]
Mar  9 19:21:27 my-laptop dhclient:                 [-sf script-file] [interface]
Mar  9 19:21:29 my-laptop avahi-daemon[1089]: Registering new address record for fe80::214:a4ff:fe60:fb61 on wlan1.*.
Mar  9 19:21:38 my-laptop kernel: [ 1728.552032] wlan1: no IPv6 routers present
```


And here it freezes.

---

### Post by gabello on 2010-03-09
Solved by adding: [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) and
[http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) to repositories and running an upgrade.

---

