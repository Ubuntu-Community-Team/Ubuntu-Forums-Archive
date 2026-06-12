---
title: "Verizon - CDMA/Novatel: Worky!  Then no worky."
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by jgreenaw on 2009-11-18
I installed a brand new 9.10 and connected a usb based air card and went to network manager, set up a connection and boom it worked.  I'm' using this box as a router, since the air card is my only internet option.  In the process of 3 days, i've shut the machine down, started it up, threw hundreds of iptable scripts at it, and changed the other interface several times.  The whole time, the connection via the modem worked flawlessly.  I got the whole thing set up last night (meaning using ufw and masquerading).  I had to reboot, because of a hung process.  After I rebooted, i've never been able to connect reliably.  It will connect, then fail.  in network manager, i have removed the connection and added it back. I have removed the modem and added back.  I have rebooted again, removed the modem & connection, and added it back.
I have put the modem in my mac, and it works.
Every time in the linux box, it connects for about 20 seconds then disconnects.  
I have done some searching, but posting earlier in my debugging process.  Since this is my only internet option, I'm in starbux posting this.
Any ideas would be great.  I can post the card model later when i get home.  
I'm going to attach the relevant syslog info.  I just don't know enough to determine what is relevant in the log.  Hopefully someone can.

Thanks.

```
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Verizon connection'
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Nov 18 08:37:07 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Nov 18 08:37:07 jgreenaw-desktop modem-manager: (ttyUSB0) opening serial device...
Nov 18 08:37:07 jgreenaw-desktop modem-manager: Got failure code 100: Unknown error
Nov 18 08:37:07 jgreenaw-desktop modem-manager: Your CDMA modem does not support +CMEE command
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Starting pppd connection
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <debug> [1258551429.305599] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <debug> [1258551429.308247] nm_ppp_manager_start(): ppp started with pid 2314
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: pppd 2.4.5 started by root, uid 0
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: Using interface ppp0
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: Connect: ppp0 <--> /dev/ttyUSB0
Nov 18 08:37:09 jgreenaw-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 18 08:37:09 jgreenaw-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: Cannot determine ethernet address for proxy ARP
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: local  IP address 75.x.y.z
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: remote IP address 66.x.y.z
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: primary   DNS address 66.x.y.z
Nov 18 08:37:09 jgreenaw-desktop pppd[2314]: secondary DNS address 66.x.y.z
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 18 08:37:09 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
Nov 18 08:37:10 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 (reason 0)
Nov 18 08:37:10 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:10 jgreenaw-desktop NetworkManager: <info>  Policy set 'Verizon connection' (ppp0) as default for routing and DNS.
Nov 18 08:37:10 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) successful, device activated.
Nov 18 08:37:10 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 18 08:37:12 jgreenaw-desktop ntpdate[2377]: adjust time server 91.189.94.4 offset 0.299710 sec
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: LCP terminated by peer
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: Connect time 0.2 minutes.
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: Sent 1464 bytes, received 986 bytes.
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: Modem hangup
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: Connection terminated.
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 8 -> 9 (reason 13)
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  Activation (ttyUSB0) failed.
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Nov 18 08:37:17 jgreenaw-desktop modem-manager: (ttyUSB0) closing serial device...
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <WARN>  monitor_cb(): Could not read ppp stats: No such device
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Nov 18 08:37:17 jgreenaw-desktop pppd[2314]: Exit.
Nov 18 08:37:17 jgreenaw-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 08:37:17 jgreenaw-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 18 08:37:20 jgreenaw-desktop NetworkManager: <debug> [1258551440.000657] ensure_killed(): waiting for ppp pid 2314 to exit
Nov 18 08:37:20 jgreenaw-desktop NetworkManager: <debug> [1258551440.000767] ensure_killed(): ppp pid 2314 cleaned up
```

---

