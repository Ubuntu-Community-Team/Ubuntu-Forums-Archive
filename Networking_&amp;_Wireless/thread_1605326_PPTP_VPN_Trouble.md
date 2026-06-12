---
title: "PPTP VPN Trouble"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by scarleo on 2010-10-25
I'm trying to connect to vpn.itshidden.com but it will not work no matter what settings. I have ticked MPPE, configured gateway, username, MSCHAP and MSCHAPv2 are ticked, using 128-bit encryption. I have tried to forward port 1723 and 1127 in my router, I have also ticked "enable PPTP PassThrough" in the router. I cannot telnet to vpn.itshidden.com. This is on Ubuntu Lucid. Can anyone help me out?

These are my logs from an unsuccessful connection attempt:
messages:
```
Oct 25 11:58:23 oscar-laptop pppd[5192]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct 25 11:58:23 oscar-laptop pppd[5192]: pppd 2.4.5 started by root, uid 0
Oct 25 11:58:23 oscar-laptop pppd[5192]: Using interface ppp0
Oct 25 11:58:23 oscar-laptop pppd[5192]: Connect: ppp0 <--> /dev/pts/2
Oct 25 11:58:23 oscar-laptop pppd[5192]: Modem hangup
Oct 25 11:58:23 oscar-laptop pppd[5192]: Connection terminated.
Oct 25 11:58:23 oscar-laptop pppd[5192]: Exit.
```daemon.log:
```
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5189
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 3
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 25 11:58:23 oscar-laptop pptp[5196]: nm-pptp-service-5189 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct 25 11:58:23 oscar-laptop pptp[5198]: nm-pptp-service-5189 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Oct 25 11:58:23 oscar-laptop pptp[5198]: nm-pptp-service-5189 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 94.75.253.244
Oct 25 11:58:23 oscar-laptop pptp[5196]: nm-pptp-service-5189 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 6
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state change reason: 0
Oct 25 11:58:23 oscar-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  Policy set 'Auto ComHem<32AC0D>' (eth0) as default for routing and DNS.
Oct 25 11:58:36 oscar-laptop NetworkManager: <debug> [1288000716.001274] ensure_killed(): waiting for vpn service pid 5189 to exit
Oct 25 11:58:36 oscar-laptop NetworkManager: <debug> [1288000716.001402] ensure_killed(): vpn service pid 5189 cleaned up

```syslog:
```
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5189
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Oct 25 11:58:17 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 3
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Oct 25 11:58:23 oscar-laptop pppd[5192]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct 25 11:58:23 oscar-laptop pppd[5192]: pppd 2.4.5 started by root, uid 0
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 25 11:58:23 oscar-laptop pppd[5192]: Using interface ppp0
Oct 25 11:58:23 oscar-laptop pppd[5192]: Connect: ppp0 <--> /dev/pts/2
Oct 25 11:58:23 oscar-laptop pptp[5196]: nm-pptp-service-5189 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct 25 11:58:23 oscar-laptop pptp[5198]: nm-pptp-service-5189 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Oct 25 11:58:23 oscar-laptop pptp[5198]: nm-pptp-service-5189 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 94.75.253.244
Oct 25 11:58:23 oscar-laptop pptp[5196]: nm-pptp-service-5189 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Oct 25 11:58:23 oscar-laptop pppd[5192]: Modem hangup
Oct 25 11:58:23 oscar-laptop pppd[5192]: Connection terminated.
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 25 11:58:23 oscar-laptop pppd[5192]: Exit.
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin failed: 1
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state changed: 6
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  VPN plugin state change reason: 0
Oct 25 11:58:23 oscar-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 25 11:58:23 oscar-laptop NetworkManager: <info>  Policy set 'Auto ComHem<32AC0D>' (eth0) as default for routing and DNS.
Oct 25 11:58:36 oscar-laptop NetworkManager: <debug> [1288000716.001274] ensure_killed(): waiting for vpn service pid 5189 to exit
Oct 25 11:58:36 oscar-laptop NetworkManager: <debug> [1288000716.001402] ensure_killed(): vpn service pid 5189 cleaned up

```

---

### Post by scarleo on 2010-10-26
Nobody knows what I should try next? Please help.

---

