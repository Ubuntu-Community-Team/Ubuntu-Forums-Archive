---
title: "Unable PN to Windows Server"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by ubunteshwar on 2012-09-27
I have Ubuntu 11.04 and I have not been able to connect to the office network. Syslog shows this:

Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]: <info> Starting VPN service 'pptp'...
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 4119
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]: <info> VPN service 'pptp' appeared; activating connections
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]: <info> VPN plugin state changed: 3
Sep 27 15:07:53 eshwar-lt2 pppd[4121]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]: <info> VPN connection 'OJC' (Connect) reply received.
Sep 27 15:07:53 eshwar-lt2 pppd[4121]: pppd 2.4.5 started by root, uid 0
Sep 27 15:07:53 eshwar-lt2 pppd[4121]: Using interface ppp0
Sep 27 15:07:53 eshwar-lt2 pppd[4121]: Connect: ppp0 <--> /dev/pts/2
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 27 15:07:53 eshwar-lt2 NetworkManager[913]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 27 15:07:53 eshwar-lt2 pptp[4124]: nm-pptp-service-4119 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep 27 15:08:24 eshwar-lt2 pppd[4121]: LCP: timeout sending Config-Requests
Sep 27 15:08:24 eshwar-lt2 pppd[4121]: Connection terminated.
Sep 27 15:08:24 eshwar-lt2 NetworkManager[913]: <warn> VPN plugin failed: 1
Sep 27 15:08:24 eshwar-lt2 avahi-daemon[911]: Withdrawing workstation service for ppp0.
Sep 27 15:08:24 eshwar-lt2 NetworkManager[913]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 27 15:08:24 eshwar-lt2 pppd[4121]: Modem hangup
Sep 27 15:08:24 eshwar-lt2 NetworkManager[913]: <warn> VPN plugin failed: 1
Sep 27 15:08:29 eshwar-lt2 pppd[4121]: Exit.
Sep 27 15:08:29 eshwar-lt2 NetworkManager[913]: <warn> VPN plugin failed: 1
Sep 27 15:08:29 eshwar-lt2 NetworkManager[913]: <info> VPN plugin state changed: 6
Sep 27 15:08:29 eshwar-lt2 NetworkManager[913]: <info> VPN plugin state change reason: 0
Sep 27 15:08:29 eshwar-lt2 NetworkManager[913]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Sep 27 15:08:29 eshwar-lt2 NetworkManager[913]: <info> Policy set 'Auto linksys' (eth1) as default for IPv4 routing and DNS.
Sep 27 15:08:34 eshwar-lt2 NetworkManager[913]: <info> VPN service 'pptp' disappeared

Thanks

---

### Post by ubunteshwar on 2012-09-27
The subject should read "Unable to VPN Windows Server"
Sorry about the typo

---

### Post by ubunteshwar on 2012-09-28
Any one here to help? Thanks

---

