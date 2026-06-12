---
title: "PPTP VPN connection is failed after awhile"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by amirjadidi on 2010-03-12
Hi,
I setup a PPTP VPN connection in ubuntu 9.10 (x86_64) using NetworkManager. After enabling the VPN connection, I can browse web pages (it's perfect) but after a while the vpn connection is terminated!
The following is my syslog after connecting and terminating:

```
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2204
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  VPN plugin state changed: 1
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  VPN plugin state changed: 3
Mar 12 22:10:10 amir-desktop NetworkManager: <info>  VPN connection 'VPN' (Connect) reply received.
Mar 12 22:10:10 amir-desktop pppd[2208]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Mar 12 22:10:10 amir-desktop pppd[2208]: pppd 2.4.5 started by root, uid 0
Mar 12 22:10:10 amir-desktop pptp[2212]: nm-pptp-service-2204 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Mar 12 22:10:10 amir-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 12 22:10:10 amir-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar 12 22:10:10 amir-desktop pppd[2208]: Using interface ppp0
Mar 12 22:10:10 amir-desktop pppd[2208]: Connect: ppp0 <--> /dev/pts/0
Mar 12 22:10:10 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Mar 12 22:10:11 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Mar 12 22:10:11 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Mar 12 22:10:11 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Mar 12 22:10:12 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Mar 12 22:10:12 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 1416).
Mar 12 22:10:13 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 33612
Mar 12 22:10:13 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Mar 12 22:10:13 amir-desktop pptp[2220]: nm-pptp-service-2204 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 12 22:10:13 amir-desktop pppd[2208]: Remote message: ^JAuthentication Successful.^J
Mar 12 22:10:13 amir-desktop pppd[2208]: PAP authentication succeeded
Mar 12 22:10:13 amir-desktop kernel: [  144.171931] PPP BSD Compression module registered
Mar 12 22:10:13 amir-desktop kernel: [  144.191753] PPP Deflate Compression module registered
Mar 12 22:10:14 amir-desktop pppd[2208]: Cannot determine ethernet address for proxy ARP
Mar 12 22:10:14 amir-desktop pppd[2208]: local  IP address 200.0.0.8
Mar 12 22:10:14 amir-desktop pppd[2208]: remote IP address 200.0.0.1
Mar 12 22:10:14 amir-desktop pppd[2208]: primary   DNS address 209.11.240.36
Mar 12 22:10:14 amir-desktop pppd[2208]: secondary DNS address 209.11.240.35
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  VPN connection 'VPN' (IP Config Get) reply received.
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  VPN Gateway: 174.139.82.88
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Tunnel Device: ppp0
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Internal IP4 Address: 200.0.0.8
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Internal IP4 Prefix: 32
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Internal IP4 Point-to-Point Address: 200.0.0.1
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Maximum Segment Size (MSS): 0
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Internal IP4 DNS: 209.11.240.36
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Internal IP4 DNS: 209.11.240.35
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  DNS Domain: '(none)'
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  Login Banner:
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  -----------------------------------------
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  (null)
Mar 12 22:10:14 amir-desktop NetworkManager: <info>  -----------------------------------------
Mar 12 22:10:15 amir-desktop NetworkManager: <info>  VPN connection 'VPN' (IP Config Get) complete.
Mar 12 22:10:15 amir-desktop NetworkManager: <info>  Policy set 'VPN' (ppp0) as default for routing and DNS.
Mar 12 22:10:15 amir-desktop NetworkManager: <info>  VPN plugin state changed: 4
Mar 12 22:10:15 amir-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar 12 22:10:21 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 47 (expecting 46, lost or reordered)
Mar 12 22:10:24 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 71 (expecting 70, lost or reordered)
Mar 12 22:10:24 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 73 (expecting 72, lost or reordered)
Mar 12 22:10:29 amir-desktop wpa_supplicant[1074]: CTRL-EVENT-SCAN-RESULTS 
Mar 12 22:10:44 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 100 (expecting 99, lost or reordered)
Mar 12 22:11:11 amir-desktop pptp[2220]: nm-pptp-service-2204 log[logecho:pptp_ctrl.c:677]: Echo Request received.
Mar 12 22:11:11 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Mar 12 22:11:29 amir-desktop wpa_supplicant[1074]: CTRL-EVENT-SCAN-RESULTS 
Mar 12 22:11:38 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 132 (expecting 131, lost or reordered)
Mar 12 22:11:38 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 136 (expecting 135, lost or reordered)
Mar 12 22:11:39 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 143 (expecting 142, lost or reordered)
Mar 12 22:11:39 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 145 (expecting 144, lost or reordered)
Mar 12 22:11:42 amir-desktop pptp[2212]: nm-pptp-service-2204 log[decaps_gre:pptp_gre.c:414]: buffering packet 151 (expecting 150, lost or reordered)
Mar 12 22:11:44 amir-desktop pptp[2212]: nm-pptp-service-2204 warn[decaps_gre:pptp_gre.c:331]: short read (-1): Message too long
Mar 12 22:11:44 amir-desktop pptp[2220]: nm-pptp-service-2204 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar 12 22:11:44 amir-desktop pptp[2220]: nm-pptp-service-2204 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar 12 22:11:44 amir-desktop pptp[2220]: nm-pptp-service-2204 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar 12 22:11:44 amir-desktop pppd[2208]: Modem hangup
Mar 12 22:11:44 amir-desktop pppd[2208]: Connect time 1.5 minutes.
Mar 12 22:11:44 amir-desktop pppd[2208]: Sent 24679 bytes, received 113964 bytes.
Mar 12 22:11:44 amir-desktop pppd[2208]: Connection terminated.
Mar 12 22:11:44 amir-desktop NetworkManager: <info>  VPN plugin state changed: 5
Mar 12 22:11:44 amir-desktop NetworkManager: <info>  VPN plugin state changed: 6
Mar 12 22:11:44 amir-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Mar 12 22:11:44 amir-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Mar 12 22:11:44 amir-desktop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Mar 12 22:11:44 amir-desktop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Mar 12 22:11:45 amir-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 12 22:11:45 amir-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 12 22:11:45 amir-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar 12 22:11:45 amir-desktop pppd[2208]: Exit.
```

Can anybody help me to solve that?
Kind regards

---

### Post by amirjadidi on 2010-03-13
Any help?! :(

---

### Post by demuxer on 2010-04-14
I need help too...

but your log has a message
Mar 12 22:10:10 amir-desktop pppd[2208]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.

are you using pptpd meaning dial-up?

my syslog is
I have the same problem, my syslog :

 NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'MyVpnProfile' failed to connect: 'No VPN secrets!'.
Apr 14 11:05:52 karmicdesktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

---

### Post by demuxer on 2010-04-28
still looking for answers!?!?

---

### Post by SinaMiandashti on 2010-09-25
same here


any fix for first post of the topic?

---

### Post by kamiar on 2011-01-05
I have same problem :|

---

### Post by behzad83 on 2011-01-13
[FONT=Times New Roman][SIZE=5]Just put a # at the front of these line in your options.pptpd :

proxyarp
nobsdcomp
nodeflate
[/SIZE][/FONT]

---

### Post by Mihai Cilidariu on 2011-01-13
I had the same problem but editing options.pptd didn't help.


This solution worked for me: [[SOLVED] PPT connects but fails]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9279383&postcount=2") (basically, decrease MTU on the 'real' network interface to about 1200).

---

### Post by nmriahi on 2013-01-25
Hi Dudes,

I had the same problem for past few days, after surfing web for solution to this problem, finally I found one that worked perfectly for me.
Please consult the following link to find out more about appropriate settings for VPN in Ubuntu GNU/Linux:
[http://vpnblog.info/ubuntu-pptp-strongvpn.html](http://vpnblog.info/ubuntu-pptp-strongvpn.html)

Hope this would work for you guys alike.

Best Wishes,
Nima

---

### Post by amirjadidi on 2013-01-25
Hi Nima,
I'm using [VPNMakers]("http://vpnmakers.tk/") which does not support this configure. The interesting thing that when querying facebook (https), it is disconnected!
When using other sites, it doesn't!
Really interesting.

---

### Post by amirjadidi on 2013-01-25
> **Mihai Cilidariu said:**
> I had the same problem but editing options.pptd didn't help.


This solution worked for me: [[SOLVED] PPT connects but fails]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9279383&postcount=2") (basically, decrease MTU on the 'real' network interface to about 1200).


It Solved the problem.

---

### Post by nmriahi on 2013-01-26
> **amirjadidi said:**
> It Solved the problem.

I tested this method as well, but unfortunately it couldn't solve my problem.

Good news that your problem solved as well

---

### Post by wildmanne39 on 2013-01-26
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old

---

