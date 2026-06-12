---
title: "VPN Access failed"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by iroy2000 on 2009-12-16
Hi all,

I'm using PPTP and was trying to connect to my office VPN from my ubuntu, but just failed.  ( VPN Connection failed )

When I click on VPN configuration for that particular VPN.

There are 2 tags ( VPN, IPV4 Setting )

I filled all the "VPN" tag stuff.

They are "Gateway, user name, password, NT Domain".

I wonder if I put in wrong stuff in those fields...

Any help would be appreciated, thanks.

```

Dec 16 11:32:15 m001 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Dec 16 11:32:15 m001 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5513
Dec 16 11:32:15 m001 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Dec 16 11:32:15 m001 NetworkManager: <info>  VPN plugin state changed: 3
Dec 16 11:32:15 m001 NetworkManager: <info>  VPN connection 'MyVPNConnection' (Connect) reply received.
Dec 16 11:32:15 m001 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 16 11:32:15 m001 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 16 11:32:15 m001 pptp[5518]: nm-pptp-service-5513 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 16 11:32:15 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 16 11:32:15 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 16 11:32:15 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 59259).
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 16 11:32:16 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Dec 16 11:32:19 m001 NetworkManager: <info>  VPN plugin failed: 1
Dec 16 11:32:19 m001 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 16 11:32:19 m001 pptp[5518]: nm-pptp-service-5513 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 16 11:32:19 m001 pptp[5518]: nm-pptp-service-5513 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 16 11:32:19 m001 pptp[5524]: nm-pptp-service-5513 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 16 11:32:19 m001 pptp[5524]: nm-pptp-service-5513 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Dec 16 11:32:19 m001 pptp[5524]: nm-pptp-service-5513 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 16 11:32:19 m001 NetworkManager: <info>  VPN plugin failed: 1
Dec 16 11:32:19 m001 NetworkManager: <info>  VPN plugin failed: 1
Dec 16 11:32:19 m001 NetworkManager: <info>  VPN plugin state changed: 6
Dec 16 11:32:19 m001 NetworkManager: <info>  VPN plugin state change reason: 0
Dec 16 11:32:19 m001 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Dec 16 11:32:19 m001 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 16 11:32:32 m001 NetworkManager: <debug> [1260991952.002423] ensure_killed(): waiting for vpn service pid 5513 to exit
Dec 16 11:32:32 m001 NetworkManager: <debug> [1260991952.002684] ensure_killed(): vpn service pid 5513 cleaned up

```

---

