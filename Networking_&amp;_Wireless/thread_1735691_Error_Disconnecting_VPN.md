---
title: "Error Disconnecting VPN"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by ClaudemarMartins on 2011-04-21
When you access the VPN service gives this error below.

**daemon.log**```
Apr 21 14:32:06 Name-Is NetworkManager[877]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Apr 21 14:32:06 Name-Is NetworkManager[877]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6303
Apr 21 14:32:06 Name-Is NetworkManager[877]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Apr 21 14:32:06 Name-Is NetworkManager[877]: <info> VPN plugin state changed: 1
Apr 21 14:32:11 Name-Is NetworkManager[877]: <info> VPN plugin state changed: 3
Apr 21 14:32:11 Name-Is NetworkManager[877]: <info> VPN connection 'SERVIÇO VPN' (Connect) reply received.
Apr 21 14:32:11 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 21 14:32:11 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 21 14:32:11 Name-Is modem-manager: (net/ppp0): could not get port's parent device
Apr 21 14:32:11 Name-Is pptp[6309]: nm-pptp-service-6303 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 21 14:32:42 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:42 Name-Is avahi-daemon[863]: Withdrawing workstation service for ppp0.
Apr 21 14:32:42 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 21 14:32:42 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:47 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> VPN plugin state changed: 6
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> VPN plugin state change reason: 0
Apr 21 14:32:47 Name-Is NetworkManager[877]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
```**debug**```
Apr 21 14:32:11 Name-Is modem-manager: (net/ppp0): could not get port's parent device
```**messages** ```
Apr 21 14:32:11 Name-Is pppd[6305]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 21 14:32:11 Name-Is pppd[6305]: pppd 2.4.5 started by root, uid 0
Apr 21 14:32:11 Name-Is pppd[6305]: Using interface ppp0
Apr 21 14:32:11 Name-Is pppd[6305]: Connect: ppp0 <--> /dev/pts/1
Apr 21 14:32:42 Name-Is pppd[6305]: LCP: timeout sending Config-Requests
Apr 21 14:32:42 Name-Is pppd[6305]: Connection terminated.
Apr 21 14:32:42 Name-Is pppd[6305]: Modem hangup
Apr 21 14:32:47 Name-Is pppd[6305]: Exit.
```**syslog**```
Apr 21 14:32:11 Name-Is NetworkManager[877]: <info> VPN plugin state changed: 3
Apr 21 14:32:11 Name-Is NetworkManager[877]: <info> VPN connection 'SERVIÇO VPN' (Connect) reply received.
Apr 21 14:32:11 Name-Is pppd[6305]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 21 14:32:11 Name-Is pppd[6305]: pppd 2.4.5 started by root, uid 0
Apr 21 14:32:11 Name-Is pppd[6305]: Using interface ppp0
Apr 21 14:32:11 Name-Is pppd[6305]: Connect: ppp0 <--> /dev/pts/1
Apr 21 14:32:11 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 21 14:32:11 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 21 14:32:11 Name-Is modem-manager: (net/ppp0): could not get port's parent device
Apr 21 14:32:11 Name-Is pptp[6309]: nm-pptp-service-6303 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 21 14:32:42 Name-Is pppd[6305]: LCP: timeout sending Config-Requests
Apr 21 14:32:42 Name-Is pppd[6305]: Connection terminated.
Apr 21 14:32:42 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:42 Name-Is avahi-daemon[863]: Withdrawing workstation service for ppp0.
Apr 21 14:32:42 Name-Is NetworkManager[877]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 21 14:32:42 Name-Is pppd[6305]: Modem hangup
Apr 21 14:32:42 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:47 Name-Is pppd[6305]: Exit.
Apr 21 14:32:47 Name-Is NetworkManager[877]: <warn> VPN plugin failed: 1
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> VPN plugin state changed: 6
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> VPN plugin state change reason: 0
Apr 21 14:32:47 Name-Is NetworkManager[877]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Apr 21 14:32:47 Name-Is NetworkManager[877]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
```

---

### Post by ClaudemarMartins on 2011-05-08
Someone ?

[[img]http://www.freeimagehosting.net/uploads/th.00809838b9.jpg[/img]](http://www.freeimagehosting.net/image.php?00809838b9.jpg) [[img]http://www.freeimagehosting.net/uploads/th.3f713c7dc6.jpg[/img]](http://www.freeimagehosting.net/image.php?3f713c7dc6.jpg)

:confused:

---

