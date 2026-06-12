---
title: "VPN / StrongVPN - Failed to connect"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Alexhir on 2008-12-30
Hello,

I'm trying to connect to a vpn using the fallowing instructions.
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

But, when I click Connect to ***** it doesnt connect.

The VPN account is fine, works perfectly on Win32 and OS X

Can some one please help ?

Thank you in advanced.
Alex H.


This might help,

Terminal Logs.
```

Dec 29 20:53:18 Pris-Mint NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Dec 29 20:53:18 Pris-Mint NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6196 
Dec 29 20:53:18 Pris-Mint NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Dec 29 20:53:18 Pris-Mint NetworkManager: <info>  VPN plugin state changed: 3 
Dec 29 20:53:18 Pris-Mint NetworkManager: <info>  VPN connection 'StrongVPN' (Connect) reply received. 
Dec 29 20:53:18 Pris-Mint pppd[6197]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 29 20:53:18 Pris-Mint modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 29 20:53:18 Pris-Mint pppd[6197]: pppd 2.4.4 started by root, uid 0
Dec 29 20:53:18 Pris-Mint pppd[6197]: Using interface ppp0
Dec 29 20:53:18 Pris-Mint pppd[6197]: Connect: ppp0 <--> /dev/pts/1
Dec 29 20:53:19 Pris-Mint pptp[6201]: nm-pptp-service-6196 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Dec 29 20:53:19 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Dec 29 20:53:19 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 29 20:53:19 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 29 20:53:20 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Dec 29 20:53:20 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 29 20:53:20 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 36019). 
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 29 20:53:21 Pris-Mint pppd[6197]: LCP terminated by peer (A^J^RD^@<M-Mt^@^@^BM-3)
Dec 29 20:53:21 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  VPN plugin failed: 1 
Dec 29 20:53:24 Pris-Mint pppd[6197]: Connection terminated.
Dec 29 20:53:24 Pris-Mint pptp[6201]: nm-pptp-service-6196 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 29 20:53:24 Pris-Mint pptp[6201]: nm-pptp-service-6196 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 29 20:53:24 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 29 20:53:24 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Dec 29 20:53:24 Pris-Mint pptp[6209]: nm-pptp-service-6196 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  VPN plugin failed: 1 
Dec 29 20:53:24 Pris-Mint pppd[6197]: Modem hangup
Dec 29 20:53:24 Pris-Mint pppd[6197]: Exit.
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  VPN plugin failed: 1 
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  VPN plugin state changed: 6 
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  VPN plugin state change reason: 0 
Dec 29 20:53:24 Pris-Mint NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Dec 29 20:53:24 Pris-Mint NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 29 20:53:36 Pris-Mint NetworkManager: <debug> [1230591216.569165] ensure_killed(): waiting for vpn service pid 6196 to exit 
Dec 29 20:53:36 Pris-Mint NetworkManager: <debug> [1230591216.569680] ensure_killed(): vpn service pid 6196 cleaned up
```

---

### Post by Alexhir on 2008-12-31
Bump :(

---

### Post by brianpeiris on 2009-01-17
This guide helped me connect to my StrongVPN account in Ubuntu 8.10 Intrepid Ibex

[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn](http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn)

---

