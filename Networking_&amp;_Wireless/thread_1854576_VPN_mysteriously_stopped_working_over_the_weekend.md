---
title: "VPN mysteriously stopped working over the weekend"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by taotree on 2011-10-04
I have been using my work VPN for years up through Friday last week. But when I tried to connect Monday morning, it failed. I have a netbook and tried it on that, it also failed. I took my netbook down to the library and was able to connect to the VPN there. So, it appears to be something in my home network or ISP which is Comcast.

The syslog for the attempt to connect is below. The big delay is right before LCP: timeout sending Config-Requests so that appears to be where it might be failing. I've done some searching, but... I'm kind of lost for what to try next. I was going to try to bypass my router and hook up my netbook direct to the cable modem but for some reason it fails to connect to the network when I tried that.

Ubuntu 11.04 and I always install any updates that pop up.

Linux dante 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


Oct  4 13:48:25 dante NetworkManager[1025]: <info> Starting VPN service 'pptp'...
Oct  4 13:48:25 dante NetworkManager[1025]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8641
Oct  4 13:48:25 dante NetworkManager[1025]: <info> VPN service 'pptp' appeared; activating connections
Oct  4 13:48:25 dante NetworkManager[1025]: <info> VPN plugin state changed: 1
Oct  4 13:48:25 dante NetworkManager[1025]: <info> VPN plugin state changed: 3
Oct  4 13:48:25 dante pppd[8643]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct  4 13:48:25 dante NetworkManager[1025]: <info> VPN connection 'Liaison' (Connect) reply received.
Oct  4 13:48:25 dante pppd[8643]: pppd 2.4.5 started by root, uid 0
Oct  4 13:48:25 dante pppd[8643]: Using interface ppp0
Oct  4 13:48:25 dante pppd[8643]: Connect: ppp0 <--> /dev/pts/3
Oct  4 13:48:25 dante pptp[8646]: nm-pptp-service-8641 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct  4 13:48:25 dante NetworkManager[1025]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  4 13:48:25 dante NetworkManager[1025]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct  4 13:48:56 dante pppd[8643]: LCP: timeout sending Config-Requests
Oct  4 13:48:56 dante pppd[8643]: Connection terminated.
Oct  4 13:48:56 dante NetworkManager[1025]: <warn> VPN plugin failed: 1
Oct  4 13:48:56 dante NetworkManager[1025]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct  4 13:48:56 dante pppd[8643]: Modem hangup
Oct  4 13:48:56 dante NetworkManager[1025]: <warn> VPN plugin failed: 1
Oct  4 13:49:01 dante pppd[8643]: Exit.
Oct  4 13:49:01 dante NetworkManager[1025]: <warn> VPN plugin failed: 1
Oct  4 13:49:01 dante NetworkManager[1025]: <info> VPN plugin state changed: 6
Oct  4 13:49:01 dante NetworkManager[1025]: <info> VPN plugin state change reason: 0
Oct  4 13:49:01 dante NetworkManager[1025]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Oct  4 13:49:01 dante NetworkManager[1025]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Oct  4 13:49:06 dante NetworkManager[1025]: <info> VPN service 'pptp' disappeared
Oct  4 13:51:34 dante pptp[8647]: nm-pptp-service-8641 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
Oct  4 13:51:34 dante pptp[8647]: nm-pptp-service-8641 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 12.159.5.2
Oct  4 13:51:34 dante pptp[8646]: nm-pptp-service-8641 fatal[open_callmgr:pptp.c:487]: Call manager exited with error 256

---

### Post by taotree on 2011-10-06
Well, I was able to connect my computer directly to the cable modem (the trick is you have to restart the cable modem every time you change what is plugged into it) and then the VPN worked. So it must have something to do with the router, or the fact that the network is NAT'ed?

But... why would it suddenly stop working?

---

