---
title: "Can't connect to a pptp vpn"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by dayv2005 on 2011-01-18
I am having trouble connecting back to my vpn at work while I'm at home. Mainly need to get our local svn repos for at home development. I successfully connected to the vpn following this tutorial[https://wiki.ubuntu.com/VPN]("https://wiki.ubuntu.com/VPN").

I am running Lucid Lynx 64bit and I followed the 9.10 section of the tutorial on setting up PPTP connection.

It worked fine. Then I walked away from my computer and it was disconnected when I came back 2 hours later. I was unable to connect back to it. I used my laptop which is running windows 7 and it connected just fine. So, now I am unable to connect to it and have no idea why. 

I viewed my system log and don't know what to do with the information. Could someone help me out on this. Thanks

My syslog shows this...
```
Jan 18 18:51:43 david-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 18 18:51:43 david-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5532
Jan 18 18:51:43 david-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 18 18:51:43 david-desktop NetworkManager: <info>  VPN plugin state changed: 1
Jan 18 18:51:47 david-desktop NetworkManager: <info>  VPN plugin state changed: 3
Jan 18 18:51:47 david-desktop NetworkManager: <info>  VPN connection 'AIM VPN' (Connect) reply received.
Jan 18 18:51:47 david-desktop pppd[5536]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan 18 18:51:47 david-desktop pppd[5536]: pppd 2.4.5 started by root, uid 0
Jan 18 18:51:47 david-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 18 18:51:47 david-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 18 18:51:47 david-desktop pppd[5536]: Using interface ppp0
Jan 18 18:51:47 david-desktop pppd[5536]: Connect: ppp0 <--> /dev/pts/1
Jan 18 18:51:47 david-desktop pptp[5540]: nm-pptp-service-5532 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 18 18:51:47 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 18 18:51:47 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 18 18:51:47 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 18 18:51:48 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 18 18:51:48 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 18 18:51:48 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 42741).
Jan 18 18:52:18 david-desktop pppd[5536]: LCP: timeout sending Config-Requests
Jan 18 18:52:18 david-desktop pppd[5536]: Connection terminated.
Jan 18 18:52:18 david-desktop NetworkManager: <info>  VPN plugin failed: 1
Jan 18 18:52:18 david-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 18 18:52:18 david-desktop pptp[5540]: nm-pptp-service-5532 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan 18 18:52:18 david-desktop pptp[5540]: nm-pptp-service-5532 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan 18 18:52:18 david-desktop pppd[5536]: Modem hangup
Jan 18 18:52:18 david-desktop pptp[5547]: nm-pptp-service-5532 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan 18 18:52:18 david-desktop pptp[5547]: nm-pptp-service-5532 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan 18 18:52:18 david-desktop pptp[5547]: nm-pptp-service-5532 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan 18 18:52:18 david-desktop pppd[5536]: Exit.
Jan 18 18:52:18 david-desktop NetworkManager: <info>  VPN plugin failed: 1
Jan 18 18:52:18 david-desktop NetworkManager: <info>  VPN plugin failed: 1
Jan 18 18:52:18 david-desktop NetworkManager: <info>  VPN plugin state changed: 6
Jan 18 18:52:18 david-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Jan 18 18:52:18 david-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan 18 18:52:18 david-desktop NetworkManager: <info>  Policy set 'Auto SOAP' (wlan0) as default for routing and DNS.
Jan 18 18:52:31 david-desktop NetworkManager: <debug> [1295394751.001581] ensure_killed(): waiting for vpn service pid 5532 to exit
Jan 18 18:52:31 david-desktop NetworkManager: <debug> [1295394751.001999] ensure_killed(): vpn service pid 5532 cleaned up
```

---

### Post by dayv2005 on 2011-01-20
I solved this issue. In case anyone else has this problem I was on an at&t wesdell modem. This modem by default isn't set in bridged mode. Had to set it to bridged mode and then handle pppoe on my router. Than was able to connect just fine.

---

