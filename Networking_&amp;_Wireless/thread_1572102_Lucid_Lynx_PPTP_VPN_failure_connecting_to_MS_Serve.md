---
title: "Lucid Lynx PPTP VPN failure connecting to MS Server"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by breley on 2010-09-10
I'm attempting to get 10.04 to connect to an SBS 2003 pptp vpn server, but for the life of me have been unable to find or implement a working solution.  System previously had 8.x and 9.x and had no difficulty connecting to same server, but on a fresh install of 10.04 cannot connect.

tail -f /var/log/syslog shows the following:

```

Sep 10 15:19:32 ubuntu NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Sep 10 15:19:32 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1730
Sep 10 15:19:32 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep 10 15:19:32 ubuntu NetworkManager: <info>  VPN plugin state changed: 1
Sep 10 15:19:32 ubuntu NetworkManager: <info>  VPN plugin state changed: 3
Sep 10 15:19:32 ubuntu NetworkManager: <info>  VPN connection 'ACG VPN' (Connect) reply received.
Sep 10 15:19:32 ubuntu pppd[1732]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep 10 15:19:32 ubuntu pppd[1732]: pppd 2.4.5 started by root, uid 0
Sep 10 15:19:32 ubuntu pppd[1732]: Using interface ppp0
Sep 10 15:19:32 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 10 15:19:32 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 10 15:19:32 ubuntu pppd[1732]: Connect: ppp0 <--> /dev/pts/0
Sep 10 15:19:32 ubuntu pptp[1736]: nm-pptp-service-1730 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep 10 15:19:32 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Sep 10 15:19:32 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Sep 10 15:19:32 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 65497).
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 37494
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Sep 10 15:19:33 ubuntu pppd[1732]: MS-CHAP authentication failed: E=691 Authentication failure
Sep 10 15:19:33 ubuntu pppd[1732]: CHAP authentication failed
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 37494
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Sep 10 15:19:33 ubuntu pptp[1743]: nm-pptp-service-1730 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Sep 10 15:19:33 ubuntu pppd[1732]: Connection terminated.
Sep 10 15:19:33 ubuntu NetworkManager: <info>  VPN plugin failed: 1
Sep 10 15:19:34 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 10 15:19:34 ubuntu pptp[1736]: nm-pptp-service-1730 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Sep 10 15:19:34 ubuntu pptp[1736]: nm-pptp-service-1730 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Sep 10 15:19:34 ubuntu NetworkManager: <info>  VPN plugin failed: 1
Sep 10 15:19:34 ubuntu pptp[1743]: nm-pptp-service-1730 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Sep 10 15:19:34 ubuntu pptp[1743]: nm-pptp-service-1730 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Sep 10 15:19:34 ubuntu pptp[1743]: nm-pptp-service-1730 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Sep 10 15:19:34 ubuntu pppd[1732]: Exit.
Sep 10 15:19:34 ubuntu NetworkManager: <info>  VPN plugin state changed: 6
Sep 10 15:19:34 ubuntu NetworkManager: <info>  VPN plugin state change reason: 0
Sep 10 15:19:34 ubuntu NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep 10 15:19:34 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Sep 10 15:19:46 ubuntu NetworkManager: <debug> [1284146386.002176] ensure_killed(): waiting for vpn service pid 1730 to exit
Sep 10 15:19:46 ubuntu NetworkManager: <debug> [1284146386.002296] ensure_killed(): vpn service pid 1730 cleaned up

```I've played around with the MPPE settings, played around with /etc/networking/interfaces (changing lo to eth0 per one or more blogger's recommendation), tried with/without saving password, leaving NT Domain blank.
I'm hoping someone can examine the log and see if there's anything that rings a bell.

TIA

---

### Post by utilitytrack on 2010-09-11
Try completely remove NetworkManager and set up the DHCP client, pptp client and routing manually.

---

