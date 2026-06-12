---
title: "Vpn/pptp"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by rabby_ on 2010-06-03
Hi,

Even the debug output for the VPN connection, that isn't established, didn't help me to find out where it's failing or what plugin is missing.

Note: With kvpnc the eth0 connection runs into troubles and does no longer reply... That's why I tried with network-manager now.

On windows OS, all I have to do, is setting up a default VPN connection, enter IP, user, pw and it works there => no cisco client or similar; just the windows tools. So I am pretty sure, my target is a ppt/Ms VPN.

Now I did the same input with the ubuntu network-manager's VPN settings and after few seconds, i see a failure message. In the syslog, the debug message I can't find a hint for solving the issue.

> Jun  4 03:08:27 duser NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun  4 03:08:27 duser NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6192
Jun  4 03:08:28 duser NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun  4 03:08:28 duser NetworkManager: <info>  VPN plugin state changed: 1
Jun  4 03:08:28 duser NetworkManager: <info>  VPN plugin state changed: 3
Jun  4 03:08:28 duser NetworkManager: <info>  VPN connection 'test' (Connect) reply received.
Jun  4 03:08:28 duser pppd[6194]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun  4 03:08:28 duser pppd[6194]: pppd 2.4.5 started by root, uid 0
Jun  4 03:08:28 duser pppd[6194]: using channel 87
Jun  4 03:08:28 duser NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun  4 03:08:28 duser NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun  4 03:08:28 duser pppd[6194]: Using interface ppp0
Jun  4 03:08:28 duser pppd[6194]: Connect: ppp0 <--> /dev/pts/0
Jun  4 03:08:28 duser pptp[6198]: nm-pptp-service-6192 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun  4 03:08:28 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun  4 03:08:28 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun  4 03:08:28 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun  4 03:08:29 duser pppd[6194]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xac3ae0a8> <pcomp> <accomp>]
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 26115).
Jun  4 03:08:29 duser pppd[6194]: rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x7ff04cbc> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:cf.a7.f4.a1.cd.fa.4b.43.86.dd.5d.77.cc.11.c9.5b.00.00.00.00]> < 17 04 01 ae>]
Jun  4 03:08:29 duser pppd[6194]: sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 01 ae>]
Jun  4 03:08:29 duser pppd[6194]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xac3ae0a8> <pcomp> <accomp>]
Jun  4 03:08:29 duser pppd[6194]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x7ff04cbc> <pcomp> <accomp> <endpoint [local:cf.a7.f4.a1.cd.fa.4b.43.86.dd.5d.77.cc.11.c9.5b.00.00.00.00]>]
Jun  4 03:08:29 duser pppd[6194]: sent [LCP ConfAck id=0x1 <mru 1400> <auth eap> <magic 0x7ff04cbc> <pcomp> <accomp> <endpoint [local:cf.a7.f4.a1.cd.fa.4b.43.86.dd.5d.77.cc.11.c9.5b.00.00.00.00]>]
Jun  4 03:08:29 duser pppd[6194]: sent [LCP EchoReq id=0x0 magic=0xac3ae0a8]
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun  4 03:08:29 duser pppd[6194]: rcvd [EAP Request id=0x3 Identity <No message>]
Jun  4 03:08:29 duser pppd[6194]: sent [EAP Response id=0x3 Identity <Name "rabby">]
Jun  4 03:08:29 duser pppd[6194]: rcvd [LCP EchoRep id=0x0 magic=0x7ff04cbc]
Jun  4 03:08:29 duser pppd[6194]: rcvd [EAP Request id=0x4 TLS 20]
Jun  4 03:08:29 duser pppd[6194]: EAP: unknown authentication type 13; Naking
Jun  4 03:08:29 duser pppd[6194]: sent [EAP Response id=0x4 Nak <Suggested-type 13>]
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jun  4 03:08:29 duser pppd[6194]: rcvd [LCP TermReq id=0x4 7f f0 4c bc 00 3c cd 74 00 00 02 b3]
Jun  4 03:08:29 duser pppd[6194]: LCP terminated by peer (^?M-pLM-<^@<M-Mt^@^@^BM-3)
Jun  4 03:08:29 duser pppd[6194]: sent [LCP TermAck id=0x4]
Jun  4 03:08:29 duser pptp[6205]: nm-pptp-service-6192 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jun  4 03:08:32 duser pppd[6194]: Connection terminated.
Jun  4 03:08:32 duser NetworkManager: <info>  VPN plugin failed: 1
Thanks a lot for advice!

---

