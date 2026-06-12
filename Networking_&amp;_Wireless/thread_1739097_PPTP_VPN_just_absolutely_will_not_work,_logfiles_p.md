---
title: "PPTP VPN just absolutely will not work, logfiles posted"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by ikillerzi on 2011-04-25
10.04 Ubuntu, Have tried every single combination of fields in the Advanced options area when setting up the VPN.  



```
Apr 25 02:48:10 John NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Apr 25 02:48:10 John NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 12263
Apr 25 02:48:10 John NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Apr 25 02:48:10 John NetworkManager: <info>  VPN plugin state changed: 1
Apr 25 02:48:10 John NetworkManager: <info>  VPN plugin state changed: 3
Apr 25 02:48:10 John NetworkManager: <info>  VPN connection 'b' (Connect) reply received.
Apr 25 02:48:10 John pppd[12265]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 25 02:48:10 John pppd[12265]: pppd 2.4.5 started by root, uid 0
Apr 25 02:48:10 John pptp[12268]: nm-pptp-service-12263 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 25 02:48:10 John NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 25 02:48:10 John NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 25 02:48:10 John pppd[12265]: Using interface ppp0
Apr 25 02:48:10 John pppd[12265]: Connect: ppp0 <--> /dev/pts/0
Apr 25 02:48:10 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Apr 25 02:48:10 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr 25 02:48:10 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr 25 02:48:11 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr 25 02:48:11 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr 25 02:48:11 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 571).
Apr 25 02:48:41 John pppd[12265]: LCP: timeout sending Config-Requests
Apr 25 02:48:41 John pppd[12265]: Connection terminated.
Apr 25 02:48:41 John NetworkManager: <info>  VPN plugin failed: 1
Apr 25 02:48:41 John NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 25 02:48:41 John pptp[12268]: nm-pptp-service-12263 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr 25 02:48:41 John pptp[12268]: nm-pptp-service-12263 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Apr 25 02:48:41 John pppd[12265]: Modem hangup
Apr 25 02:48:41 John pptp[12276]: nm-pptp-service-12263 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr 25 02:48:41 John pptp[12276]: nm-pptp-service-12263 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr 25 02:48:41 John pptp[12276]: nm-pptp-service-12263 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 25 02:48:41 John NetworkManager: <info>  VPN plugin failed: 1
Apr 25 02:48:41 John pppd[12265]: Exit.
Apr 25 02:48:41 John NetworkManager: <info>  VPN plugin failed: 1
Apr 25 02:48:41 John NetworkManager: <info>  VPN plugin state changed: 6
Apr 25 02:48:41 John NetworkManager: <info>  VPN plugin state change reason: 0
Apr 25 02:48:41 John NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Apr 25 02:48:41 John NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 25 02:48:54 John NetworkManager: <debug> [1303717734.001204] ensure_killed(): waiting for vpn service pid 12263 to exit
Apr 25 02:48:54 John NetworkManager: <debug> [1303717734.001290] ensure_killed(): vpn service pid 12263 cleaned up

```

---

### Post by mattpatey on 2011-05-02
Hi,

I don't know whether this will work for you, but I have been trying to connect to a VPN network all day and I have finally got it working, so I can tell you what worked for me.

In windows the VPN connection worked fine, with the connection status showing a PPTP connection with MS-CHAP v2 authentification, MPPE128 encryption and no software compression.

In ubuntu 11.04 I followed the following instructions in this link:

[https://wiki.ubuntu.com/VPN#VPN%20Setup%20in%20Ubuntu%209.10](https://wiki.ubuntu.com/VPN#VPN%20Setup%20in%20Ubuntu%209.10)

It didn't work at all and my log file looked very similar to yours.

I tried pinging the vpn server without any success. I didn't think much of this because I couldn't get a ping response in Windows either and the VPN worked in Windows. However I have just tried the VPN on a different internet connection and it works fine (and I can ping the vpn server).

So, in short I don't know exactly why it is working now, but perhaps if the setup instructions in that wiki don't work then you could try pinging the server / try another internet connection to see if it works there.

---

