---
title: "pptpd oddity"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by deadite66 on 2010-11-26
Not sure if this is more of a Orange UK problem.

At home on 3G pptp works but at work on 3G i can't connect.

Working:
```
Nov 24 22:20:20 sakura pptpd[5313]: CTRL: Client 109.180.14.37 control connection started
Nov 24 22:20:20 sakura pptpd[5313]: CTRL: Starting call (launching pppd, opening GRE)
Nov 24 22:20:20 sakura pppd[5315]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Nov 24 22:20:20 sakura pppd[5315]: pppd 2.4.5 started by root, uid 0
Nov 24 22:20:20 sakura modem-manager: (net/ppp0): could not get port's parent device
Nov 24 22:20:20 sakura NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 24 22:20:20 sakura NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 24 22:20:20 sakura pppd[5315]: Using interface ppp0
Nov 24 22:20:20 sakura pppd[5315]: Connect: ppp0 <--> /dev/pts/2
Nov 24 22:20:20 sakura pptpd[5313]: GRE: Bad checksum from pppd.
Nov 24 22:20:26 sakura pppd[5315]: MPPE 128-bit stateless compression enabled
Nov 24 22:20:26 sakura pppd[5315]: found interface eth0 for proxy arp
Nov 24 22:20:26 sakura pppd[5315]: local  IP address 192.168.0.100
Nov 24 22:20:26 sakura pppd[5315]: remote IP address 192.168.0.110
Nov 24 22:20:46 sakura pppd[5315]: LCP terminated by peer (MPPE disabled)
Nov 24 22:20:46 sakura pppd[5315]: Connect time 0.4 minutes.
Nov 24 22:20:46 sakura pppd[5315]: Sent 0 bytes, received 0 bytes.
Nov 24 22:20:47 sakura pptpd[5313]: CTRL: EOF or bad error reading ctrl packet length.
Nov 24 22:20:47 sakura pptpd[5313]: CTRL: couldn't read packet header (exit)
Nov 24 22:20:47 sakura pptpd[5313]: CTRL: CTRL read failed
Nov 24 22:20:47 sakura pptpd[5313]: CTRL: Reaping child PPP[5315]
Nov 24 22:20:47 sakura pppd[5315]: Modem hangup
Nov 24 22:20:47 sakura pppd[5315]: Connection terminated.
Nov 24 22:20:47 sakura avahi-daemon[856]: Withdrawing workstation service for ppp0.
Nov 24 22:20:47 sakura NetworkManager[847]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 24 22:20:47 sakura pppd[5315]: Exit.

```

Non-Working:
```
Nov 24 18:23:08 sakura pptpd[17979]: CTRL: Client 109.181.154.2 control connection started
Nov 24 18:23:08 sakura pptpd[17979]: CTRL: Starting call (launching pppd, opening GRE)
Nov 24 18:23:08 sakura pppd[17980]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Nov 24 18:23:08 sakura pppd[17980]: pppd 2.4.5 started by root, uid 0
Nov 24 18:23:08 sakura modem-manager: (net/ppp0): could not get port's parent device
Nov 24 18:23:09 sakura NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 24 18:23:09 sakura NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 24 18:23:09 sakura pppd[17980]: Using interface ppp0
Nov 24 18:23:09 sakura pppd[17980]: Connect: ppp0 <--> /dev/pts/0
Nov 24 18:23:09 sakura pptpd[17979]: GRE: Bad checksum from pppd.
Nov 24 18:23:39 sakura pppd[17980]: LCP: timeout sending Config-Requests
Nov 24 18:23:39 sakura pppd[17980]: Connection terminated.
Nov 24 18:23:39 sakura avahi-daemon[856]: Withdrawing workstation service for ppp0.
Nov 24 18:23:39 sakura NetworkManager[847]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 24 18:23:39 sakura pppd[17980]: Modem hangup
Nov 24 18:23:39 sakura pppd[17980]: Exit.

```

Server is Ubuntu maverick, client is a Desire HD, android 2.2
Why would it work in one location but not another.

Any ideas?

---

