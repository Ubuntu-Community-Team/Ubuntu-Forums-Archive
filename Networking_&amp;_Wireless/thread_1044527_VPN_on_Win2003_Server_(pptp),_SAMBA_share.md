---
title: "VPN on Win2003 Server (pptp), SAMBA share"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by tobitious on 2009-01-19
dear all,

i want to connect to a win 2003 server vpn (pptp). for that ive setup a new Ubuntu 8.10 (Intrepid Ibex) box.
i ve searched the web how to connect to the vpn and found a soultion through the standard network manager.

after ive entered my settings and connected to the vpn, the connection seems to be online. but when i try to ping the server or to establish a smp mount, i dont get any answer.

her i give you the information syslog is giving me:
```
Jan 19 14:30:50 svbp NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Jan 19 14:30:50 svbp NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6165 
Jan 19 14:30:50 svbp NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Jan 19 14:30:50 svbp NetworkManager: <info>  VPN plugin state changed: 1 
Jan 19 14:30:50 svbp NetworkManager: <info>  VPN plugin state changed: 3 
Jan 19 14:30:50 svbp NetworkManager: <info>  VPN connection 'MEINVPN' (Connect) reply received. 
Jan 19 14:30:50 svbp pppd[6168]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Jan 19 14:30:50 svbp pppd[6168]: pppd 2.4.4 started by root, uid 0
Jan 19 14:30:50 svbp pppd[6168]: Using interface ppp0
Jan 19 14:30:50 svbp pppd[6168]: Connect: ppp0 <--> /dev/pts/0
Jan 19 14:30:50 svbp pptp[6170]: nm-pptp-service-6165 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Jan 19 14:30:51 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jan 19 14:30:51 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 19 14:30:51 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 19 14:30:52 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jan 19 14:30:52 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 19 14:30:52 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 9247). 
Jan 19 14:30:52 svbp pptp[6170]: nm-pptp-service-6165 log[decaps_gre:pptp_gre.c:405]: discarding duplicate or old packet 0 (expecting 2)
Jan 19 14:30:55 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 64655
Jan 19 14:30:55 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jan 19 14:30:55 svbp pptp[6177]: nm-pptp-service-6165 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jan 19 14:30:55 svbp pppd[6168]: CHAP authentication succeeded
Jan 19 14:30:55 svbp pppd[6168]: MPPE 128-bit stateless compression enabled
Jan 19 14:30:57 svbp pppd[6168]: found interface eth0 for proxy arp
Jan 19 14:30:57 svbp pppd[6168]: local  IP address 192.168.1.106
Jan 19 14:30:57 svbp pppd[6168]: remote IP address 192.168.1.105
Jan 19 14:30:57 svbp pppd[6168]: primary   DNS address 192.168.1.254
Jan 19 14:30:57 svbp NetworkManager: <info>  VPN connection 'MEINVPN' (IP Config Get) reply received. 
Jan 19 14:30:57 svbp NetworkManager: <info>  VPN Gateway: 192.168.1.105 
Jan 19 14:30:57 svbp NetworkManager: <info>  Tunnel Device: ppp0 
Jan 19 14:30:57 svbp NetworkManager: <info>  Internal IP4 Address: 192.168.1.106 
Jan 19 14:30:57 svbp NetworkManager: <info>  Internal IP4 Prefix: 32 
Jan 19 14:30:57 svbp NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Jan 19 14:30:57 svbp NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Jan 19 14:30:57 svbp NetworkManager: <info>  Internal IP4 DNS: 192.168.1.254 
Jan 19 14:30:57 svbp NetworkManager: <info>  DNS Domain: '(none)' 
Jan 19 14:30:57 svbp NetworkManager: <info>  Login Banner: 
Jan 19 14:30:57 svbp NetworkManager: <info>  ----------------------------------------- 
Jan 19 14:30:57 svbp NetworkManager: <info>  (null) 
Jan 19 14:30:57 svbp NetworkManager: <info>  ----------------------------------------- 
Jan 19 14:30:58 svbp NetworkManager: <info>  VPN connection 'MEINVPN' (IP Config Get) complete. 
Jan 19 14:30:58 svbp NetworkManager: <info>  Policy set 'MEINVPN' (ppp0) as default for routing and DNS. 
Jan 19 14:30:58 svbp NetworkManager: <info>  VPN plugin state changed: 4 
Jan 19 14:30:58 svbp nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jan 19 14:31:24 svbp pptp[6170]: nm-pptp-service-6165 log[decaps_gre:pptp_gre.c:414]: buffering packet 18 (expecting 17, lost or reordered)
Jan 19 14:31:51 svbp pptp[6177]: nm-pptp-service-6165 log[logecho:pptp_ctrl.c:677]: Echo Request received.
Jan 19 14:31:51 svbp pptp[6177]: nm-pptp-service-6165 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
```

when i try to connect to the vpn via mac os x or windows everything works like a charm, so i guess the problem might be on the ubuntu configuration side.

has anybody any idea about this? i am happy to provide more information on this, i just dont know what is helping. so please let me know when you need anything else.

thanks in adavance for help.

best regards,

tobias

---

### Post by tobitious on 2009-01-20
ive installed hardy and with that it works. there seem to be some problems in Ubuntu 8.10 (Intrepid Ibex) with pptp vpn.

best,

tobias

---

