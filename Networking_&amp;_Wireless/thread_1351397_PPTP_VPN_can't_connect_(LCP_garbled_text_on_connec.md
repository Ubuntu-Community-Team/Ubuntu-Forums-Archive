---
title: "PPTP VPN can't connect (LCP garbled text on connect)"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Truami on 2009-12-10
Hi,

I've been searching the forums, but have failed to find a solution for this problem.

I am trying to connect to my office VPN in Karmic, I even got them as far as to open up PPTP next to their L2TP/IPSec (which I gave up on).

Now, I've tried this in network-manager, after installing network-manager-pptp. I've also tried this in Kvpnc, because I thought NM might have a bug.

I highlighted the difference in syslog output between correct en incorrect credentials, just to check that this wasn't the issue.

**NM: Syslog output with wrong credentials:**

```
Dec 10 21:02:56 bender NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Dec 10 21:02:56 bender NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 17849
Dec 10 21:02:56 bender NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Dec 10 21:02:56 bender pppd[17852]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Dec 10 21:02:56 bender NetworkManager: <info>  VPN plugin state changed: 3
Dec 10 21:02:56 bender NetworkManager: <info>  VPN connection 'Xxx' (Connect) reply received.
Dec 10 21:02:56 bender pppd[17852]: pppd 2.4.5 started by root, uid 0
Dec 10 21:02:56 bender pppd[17852]: using channel 18
Dec 10 21:02:56 bender pppd[17852]: Using interface ppp0
Dec 10 21:02:56 bender pppd[17852]: Connect: ppp0 <--> /dev/pts/3
Dec 10 21:02:56 bender NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 21:02:56 bender NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 10 21:02:56 bender pptp[17854]: nm-pptp-service-17849 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 10 21:02:56 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 10 21:02:56 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 10 21:02:56 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 10 21:02:57 bender pppd[17852]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xad9f3a0b> <pcomp> <accomp>]
Dec 10 21:02:57 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 10 21:02:57 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 10 21:02:57 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 64640).
Dec 10 21:02:57 bender pptp[17854]: nm-pptp-service-17849 log[decaps_gre:pptp_gre.c:405]: discarding duplicate or old packet 0 (expecting 2)
Dec 10 21:02:57 bender pppd[17852]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xad9f3a0b> <pcomp> <accomp>]
Dec 10 21:02:59 bender pppd[17852]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth chap MS-v2> <magic 0x75125d85> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]> < 17 04 00 53>]
Dec 10 21:02:59 bender pppd[17852]: sent [LCP ConfRej id=0x1 <callback CBCP> <mrru 1614> < 17 04 00 53>]
Dec 10 21:02:59 bender pppd[17852]: rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x75125d85> <pcomp> <accomp> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]>]
Dec 10 21:02:59 bender pppd[17852]: sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x75125d85> <pcomp> <accomp> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]>]
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 10 21:02:59 bender pppd[17852]: rcvd [CHAP Challenge id=0x0 <3d6adcbce27299a8ecb53359ffbc1d89>, name = "ACCOUNT"]
[B]Dec 10 21:02:59 bender pppd[17852]: sent [CHAP Response id=0x0 <4e4bcfce62b63a0b9160faf3319fb16b0000000000000000fb89c0b1a09715ac1e9ec5ccc4a5495d1f4d7191bc03a76b00>, name = "XXX\\erikff"]
Dec 10 21:02:59 bender pppd[17852]: rcvd [CHAP Failure id=0x0 "E=691 R=1 C=9CCAA040087BC5FCF3A77E25B0AEC7D6 V=3"]
Dec 10 21:02:59 bender pppd[17852]: MS-CHAP authentication failed: E=691 Authentication failure[/B]
Dec 10 21:02:59 bender pppd[17852]: CHAP authentication failed
Dec 10 21:02:59 bender pppd[17852]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 10 21:02:59 bender pppd[17852]: rcvd [LCP TermAck id=0x2 "Failed to authenticate ourselves to peer"]
Dec 10 21:02:59 bender pppd[17852]: Connection terminated.
Dec 10 21:02:59 bender NetworkManager: <info>  VPN plugin failed: 1
Dec 10 21:02:59 bender NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 21:02:59 bender pppd[17852]: Waiting for 1 child processes...
Dec 10 21:02:59 bender pptp[17854]: nm-pptp-service-17849 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 10 21:02:59 bender pptp[17854]: nm-pptp-service-17849 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 10 21:02:59 bender NetworkManager: <info>  VPN plugin failed: 1
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Dec 10 21:02:59 bender pptp[17860]: nm-pptp-service-17849 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 10 21:02:59 bender pppd[17852]:   script /usr/sbin/pptp xxx.xxx.nl --nolaunchpppd --logstring nm-pptp-service-17849, pid 17853
Dec 10 21:02:59 bender pppd[17852]: Script /usr/sbin/pptp xxx.xxx.nl --nolaunchpppd --logstring nm-pptp-service-17849 finished (pid 17853), status = 0x0
Dec 10 21:02:59 bender pppd[17852]: Exit.
Dec 10 21:02:59 bender NetworkManager: <info>  VPN plugin state changed: 6
Dec 10 21:02:59 bender NetworkManager: <info>  VPN plugin state change reason: 0
Dec 10 21:02:59 bender NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Dec 10 21:02:59 bender NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.

```

**NM: Syslog output with correct credentials:**

```
Dec 10 21:01:43 bender pppd[17396]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Dec 10 21:01:43 bender NetworkManager: <info>  VPN plugin state changed: 3
Dec 10 21:01:43 bender pppd[17396]: pppd 2.4.5 started by root, uid 0
Dec 10 21:01:43 bender NetworkManager: <info>  VPN connection 'Xxx' (Connect) reply received.
Dec 10 21:01:43 bender pppd[17396]: using channel 17
Dec 10 21:01:43 bender NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 21:01:43 bender NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 10 21:01:43 bender pppd[17396]: Using interface ppp0
Dec 10 21:01:43 bender pppd[17396]: Connect: ppp0 <--> /dev/pts/3
Dec 10 21:01:43 bender pptp[17398]: nm-pptp-service-17297 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 10 21:01:43 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 10 21:01:43 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 10 21:01:43 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 10 21:01:44 bender pppd[17396]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb5290360> <pcomp> <accomp>]
Dec 10 21:01:44 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 10 21:01:44 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 10 21:01:44 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 12021).
Dec 10 21:01:44 bender pptp[17398]: nm-pptp-service-17297 log[decaps_gre:pptp_gre.c:405]: discarding duplicate or old packet 0 (expecting 2)
Dec 10 21:01:44 bender pppd[17396]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb5290360> <pcomp> <accomp>]
Dec 10 21:01:46 bender pppd[17396]: rcvd [LCP ConfReq id=0x1 <mru 1400> <auth chap MS-v2> <magic 0x4fad18ad> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]> < 17 04 00 52>]
Dec 10 21:01:46 bender pppd[17396]: sent [LCP ConfRej id=0x1 <callback CBCP> <mrru 1614> < 17 04 00 52>]
Dec 10 21:01:46 bender pppd[17396]: rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x4fad18ad> <pcomp> <accomp> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]>]
Dec 10 21:01:46 bender pppd[17396]: sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x4fad18ad> <pcomp> <accomp> <endpoint [local:06.d2.ad.41.79.c7.4b.15.9d.d7.7d.ee.06.a2.ad.3d.00.00.00.00]>]
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 10 21:01:46 bender pppd[17396]: rcvd [CHAP Challenge id=0x0 <f1c3f392787cfe6bba2c5f7dfb7f68f8>, name = "ACCOUNT"]
Dec 10 21:01:46 bender pppd[17396]: sent [CHAP Response id=0x0 <9f09418e059a1f7c8d9075fbda349b83000000000000000014b7164ce8fb10ffccfa072646a97ca760d5fd30eacf0f7600>, name = "XXX\\erik"]
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
[B]Dec 10 21:01:46 bender pppd[17396]: rcvd [LCP TermReq id=0x4 "O\37777777655\030\37777777655\000<\37777777715t\000\000\002\37777777663"]
Dec 10 21:01:46 bender pppd[17396]: LCP terminated by peer (OM--^XM--^@<M-Mt^@^@^BM-3)[/B]
Dec 10 21:01:46 bender pppd[17396]: sent [LCP TermAck id=0x4]
Dec 10 21:01:46 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Dec 10 21:01:49 bender pppd[17396]: Connection terminated.
Dec 10 21:01:49 bender NetworkManager: <info>  VPN plugin failed: 1
Dec 10 21:01:49 bender NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 21:01:49 bender pppd[17396]: Modem hangup
Dec 10 21:01:49 bender pppd[17396]: Waiting for 1 child processes...
Dec 10 21:01:49 bender pppd[17396]:   script /usr/sbin/pptp xxx.xxx.nl --nolaunchpppd --logstring nm-pptp-service-17297, pid 17397
Dec 10 21:01:49 bender pptp[17398]: nm-pptp-service-17297 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 10 21:01:49 bender pptp[17398]: nm-pptp-service-17297 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 10 21:01:49 bender pppd[17396]: Script /usr/sbin/pptp xxx.xxx.nl --nolaunchpppd --logstring nm-pptp-service-17297 finished (pid 17397), status = 0x0
Dec 10 21:01:49 bender pppd[17396]: Exit.
Dec 10 21:01:49 bender pptp[17404]: nm-pptp-service-17297 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 10 21:01:49 bender pptp[17404]: nm-pptp-service-17297 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Dec 10 21:01:49 bender pptp[17404]: nm-pptp-service-17297 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 10 21:01:49 bender NetworkManager: <info>  VPN plugin failed: 1
Dec 10 21:01:49 bender NetworkManager: <info>  VPN plugin state changed: 6
Dec 10 21:01:49 bender NetworkManager: <info>  VPN plugin state change reason: 0
Dec 10 21:01:49 bender NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Dec 10 21:01:49 bender NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.

```

Also, I found some information at the [PPTP client website]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_term_garbled"):
```
Your pppd could not negotiate encryption. Enable debug logging, try the connection again, and look for rejection packets just prior to this message. Decide what to do based on the rejection packets.
```

But, the rejection packets are garbled code. :(

Does anyone have an idea how I can fix this?

---

