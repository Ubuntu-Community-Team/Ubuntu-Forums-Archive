---
title: "VPN connection to a Windows server fails (and no posted solution worked)"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by Isilando on 2009-03-07
I try to connect to a VPN server using the network-manager applet and pptp but it fails no matter what combination of settings I use. I even tried the updated version of nm-applet and its dependencies from the PPA, but the connection still fails.

Below is the relevant section of /var/log/syslog :

[FONT="Courier New"]Mar 7 01:53:56 fakedream pppd[5705]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Mar 7 01:53:56 fakedream kernel: [ 231.929083] PPP generic driver version 2.4.2
Mar 7 01:53:56 fakedream pppd[5705]: pppd 2.4.4 started by root, uid 0
Mar 7 01:53:56 fakedream pptp[5713]: nm-pptp-service-5701 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Mar 7 01:53:56 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Mar 7 01:53:56 fakedream pppd[5705]: Using interface ppp0
Mar 7 01:53:56 fakedream pppd[5705]: Connect: ppp0 <--> /dev/pts/2
Mar 7 01:53:56 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Mar 7 01:53:56 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 47932).
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:953]: send_accm is 00000000, recv_accm is FFFFFFFF
Mar 7 01:53:57 fakedream pptp[5725]: nm-pptp-service-5701 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 7 01:53:58 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar 7 01:53:58 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:953]: send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Mar 7 01:53:58 fakedream pptp[5725]: nm-pptp-service-5701 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 7 01:53:58 fakedream pppd[5705]: LCP terminated by peer (I5jX^@<M-Mt^@^@^BM-3)
Mar 7 01:53:58 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Mar 7 01:54:01 fakedream NetworkManager: <info> VPN plugin failed: 1
Mar 7 01:54:01 fakedream pppd[5705]: Connection terminated.
Mar 7 01:54:01 fakedream pptp[5713]: nm-pptp-service-5701 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Mar 7 01:54:01 fakedream pptp[5713]: nm-pptp-service-5701 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Mar 7 01:54:01 fakedream pptp[5725]: nm-pptp-service-5701 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar 7 01:54:01 fakedream pptp[5725]: nm-pptp-service-5701 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar 7 01:54:01 fakedream pptp[5725]: nm-pptp-service-5701 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar 7 01:54:01 fakedream NetworkManager: <info> VPN plugin failed: 1
Mar 7 01:54:01 fakedream pppd[5705]: Modem hangup
Mar 7 01:54:01 fakedream pppd[5705]: Exit.[/FONT]

Could someone please help me or at least explain what is wrong? I really have no idea about network protocols, so I can't see what is wrong.

Thanks in advance.

---

