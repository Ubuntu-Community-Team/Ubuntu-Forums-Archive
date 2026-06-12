---
title: "Troubleshooting connecting to MS VPN"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by RayDeCampo on 2009-06-01
I am trying to connect to a MS VPN which I have successfully connected to in the past.  At some point my configuration became corrupted (e.g. the VPN tab does not show in Network Manager when I edit the config) so I am starting over with a fresh configuration.  I am running Ubuntu 8.10.

On the VPN tab, I have the VPN server IP under Gateway, and my username and domain entered.  Under the advanced button, I have PAP unchecked, CHAP, MSCHAP and MSCHAPv2 all checked.  I have checked use MPPE, selected "All Available" under security and checked to allow stateful encryption.  I have checked the remaining boxes as well (BSD compression, deflate compression, TCP header compression and send PPP echo packets).

The VPN server is a Windows 2003 Server with all patches applied.

Here is the output in syslog when I try to connect:

```

Jun  1 14:31:19 stingray NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Jun  1 14:31:19 stingray NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 12946 
Jun  1 14:31:19 stingray NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Jun  1 14:31:23 stingray NetworkManager: <info>  VPN plugin state changed: 3 
Jun  1 14:31:23 stingray pppd[12950]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Jun  1 14:31:23 stingray pppd[12950]: pppd 2.4.4 started by root, uid 0
Jun  1 14:31:23 stingray pppd[12950]: using channel 15
Jun  1 14:31:23 stingray pppd[12950]: Using interface ppp0
Jun  1 14:31:23 stingray pppd[12950]: Connect: ppp0 <--> /dev/pts/2
Jun  1 14:31:23 stingray NetworkManager: <info>  VPN connection 'Test' (Connect) reply received. 
Jun  1 14:31:23 stingray pptp[12953]: nm-pptp-service-12946 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Jun  1 14:31:23 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun  1 14:31:23 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun  1 14:31:23 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun  1 14:31:24 stingray pppd[12950]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x82ea5f33> <pcomp> <accomp>]
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 16990). 
Jun  1 14:31:24 stingray pppd[12950]: rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0xf3b01af> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:38.3f.16.f3.a2.23.41.77.b8.1a.c7.ff.a7.53.16.89.00.00.00.00]> < 17 04 00 13>]
Jun  1 14:31:24 stingray pppd[12950]: sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 00 13>]
Jun  1 14:31:24 stingray pppd[12950]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x82ea5f33> <pcomp> <accomp>]
Jun  1 14:31:24 stingray pppd[12950]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0xf3b01af> <pcomp> <accomp> <endpoint [local:38.3f.16.f3.a2.23.41.77.b8.1a.c7.ff.a7.53.16.89.00.00.00.00]>]
Jun  1 14:31:24 stingray pppd[12950]: sent [LCP ConfAck id=0x1 <mru 1400> <auth eap> <magic 0xf3b01af> <pcomp> <accomp> <endpoint [local:38.3f.16.f3.a2.23.41.77.b8.1a.c7.ff.a7.53.16.89.00.00.00.00]>]
Jun  1 14:31:24 stingray pppd[12950]: sent [LCP EchoReq id=0x0 magic=0x82ea5f33]
Jun  1 14:31:24 stingray pppd[12950]: rcvd [EAP Request id=0x8 Identity <No message>]
Jun  1 14:31:24 stingray pppd[12950]: sent [EAP Response id=0x8 Identity <Name "stingray">]
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun  1 14:31:24 stingray pppd[12950]: rcvd [LCP EchoRep id=0x0 magic=0xf3b01af]
Jun  1 14:31:24 stingray pppd[12950]: rcvd [LCP TermReq id=0x3 0f 3b 01 af 00 3c cd 74 00 00 02 b3]
Jun  1 14:31:24 stingray pppd[12950]: LCP terminated by peer (^O;^AM-/^@<M-Mt^@^@^BM-3)
Jun  1 14:31:24 stingray pppd[12950]: sent [LCP TermAck id=0x3]
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun  1 14:31:24 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jun  1 14:31:27 stingray pppd[12950]: Connection terminated.
Jun  1 14:31:27 stingray NetworkManager: <info>  VPN plugin failed: 1 
Jun  1 14:31:27 stingray pptp[12953]: nm-pptp-service-12946 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jun  1 14:31:27 stingray pptp[12953]: nm-pptp-service-12946 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jun  1 14:31:27 stingray pptp[12959]: nm-pptp-service-12946 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jun  1 14:31:27 stingray pptp[12959]: nm-pptp-service-12946 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jun  1 14:31:27 stingray pptp[12959]: nm-pptp-service-12946 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jun  1 14:31:27 stingray pppd[12950]: Script /usr/sbin/pptp 1.1.1.1 --nolaunchpppd --logstring nm-pptp-service-12946 finished (pid 12951), status = 0x0
Jun  1 14:31:27 stingray pppd[12950]: Modem hangup
Jun  1 14:31:27 stingray NetworkManager: <info>  VPN plugin failed: 1 
Jun  1 14:31:27 stingray pppd[12950]: Exit.
Jun  1 14:31:27 stingray NetworkManager: <info>  VPN plugin failed: 1 
Jun  1 14:31:27 stingray NetworkManager: <info>  VPN plugin state changed: 6 
Jun  1 14:31:27 stingray NetworkManager: <info>  VPN plugin state change reason: 0 
Jun  1 14:31:27 stingray NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Jun  1 14:31:27 stingray NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Jun  1 14:31:39 stingray NetworkManager: <debug> [1243881099.448326] ensure_killed(): waiting for vpn service pid 12946 to exit 
Jun  1 14:31:39 stingray NetworkManager: <debug> [1243881099.448527] ensure_killed(): vpn service pid 12946 cleaned up 

```

---

### Post by RayDeCampo on 2009-06-03
Anybody know a better place to ask this question?

---

