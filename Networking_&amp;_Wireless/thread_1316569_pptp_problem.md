---
title: "pptp problem"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by aLiEnTxC on 2009-11-06
Hi,

I try to make an pptp connection over Network-Manager Plugin from Ubuntu 9.10

On my home Network it works like a charm.

But at work I only get Errors. We can think, that the Router on this Network is not properly configured or block something, but no! On Windows it works. So the error is somewhere else.

Thats the log which I get, when I try to connect:

```
Nov  6 09:12:50 nb NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov  6 09:12:50 nb NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 4094
Nov  6 09:12:50 nb NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Nov  6 09:12:50 nb NetworkManager: <info>  VPN plugin state changed: 1
Nov  6 09:12:50 nb NetworkManager: <info>  VPN plugin state changed: 3
Nov  6 09:12:50 nb pppd[4097]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov  6 09:12:50 nb pppd[4097]: pppd 2.4.5 started by root, uid 0
Nov  6 09:12:50 nb NetworkManager: <info>  VPN connection 'my.dyndns.org' (Connect) reply received.
Nov  6 09:12:50 nb pppd[4097]: Using interface ppp0
Nov  6 09:12:50 nb pppd[4097]: Connect: ppp0 <--> /dev/pts/1
Nov  6 09:12:50 nb NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  6 09:12:50 nb NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov  6 09:12:50 nb pptp[4099]: nm-pptp-service-4094 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov  6 09:12:50 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov  6 09:12:50 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov  6 09:12:50 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov  6 09:12:51 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov  6 09:12:51 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov  6 09:12:51 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 18542).
Nov  6 09:13:21 nb pppd[4097]: LCP: timeout sending Config-Requests
Nov  6 09:13:21 nb pppd[4097]: Connection terminated.
Nov  6 09:13:21 nb NetworkManager: <info>  VPN plugin failed: 1
Nov  6 09:13:21 nb NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  6 09:13:21 nb pptp[4099]: nm-pptp-service-4094 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Nov  6 09:13:21 nb pppd[4097]: Modem hangup
Nov  6 09:13:21 nb pptp[4099]: nm-pptp-service-4094 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Nov  6 09:13:21 nb pptp[4105]: nm-pptp-service-4094 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Nov  6 09:13:21 nb pptp[4105]: nm-pptp-service-4094 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov  6 09:13:21 nb pptp[4105]: nm-pptp-service-4094 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov  6 09:13:21 nb NetworkManager: <info>  VPN plugin failed: 1
Nov  6 09:13:21 nb pppd[4097]: Exit.
Nov  6 09:13:21 nb NetworkManager: <info>  VPN plugin failed: 1
Nov  6 09:13:21 nb NetworkManager: <info>  VPN plugin state changed: 6
Nov  6 09:13:21 nb NetworkManager: <info>  VPN plugin state change reason: 0
Nov  6 09:13:21 nb NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov  6 09:13:21 nb NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
Nov  6 09:13:21 nb NetworkManager: <info>  Policy set 'Auto WLAN' (wlan0) as default for routing and DNS.
Nov  6 09:13:34 nb NetworkManager: <debug> [1257495214.002091] ensure_killed(): waiting for vpn service pid 4094 to exit
Nov  6 09:13:34 nb NetworkManager: <debug> [1257495214.002245] ensure_killed(): vpn service pid 4094 cleaned up
```

Something is whrong... but I dont have an idea what it can be...?!

this is the tcpdump output:
```
user@nb:~$ sudo tcpdump -i wlan0 host XX.XX.XXX.XXX
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
09:36:42.750088 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [S], seq 113061659, win 5840, options [mss 1460,sackOK,TS val 629851 ecr 0,nop,wscale 6], length 0
09:36:42.779637 IP my.dyndns.org.1723 > nb.firma.de.54686: Flags [S.], seq 3532139035, ack 113061660, win 16384, options [mss 1452,nop,wscale 0,nop,nop,TS val 0 ecr 0,nop,nop,sackOK], length 0
09:36:42.779690 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [.], ack 1, win 92, options [nop,nop,TS val 629858 ecr 0], length 0
09:36:42.780993 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [P.], seq 1:157, ack 1, win 92, options [nop,nop,TS val 629858 ecr 0], length 156: pptp CTRL_MSGTYPE=SCCRQ PROTO_VER(1.0) FRAME_CAP(AS) BEARER_CAP(DA) [|pptp]
09:36:42.815415 IP my.dyndns.org.1723 > nb.firma.de.54686: Flags [P.], seq 1:157, ack 157, win 65379, options [nop,nop,TS val 102184050 ecr 629851], length 156: pptp CTRL_MSGTYPE=SCCRP PROTO_VER(1.0) RESULT_CODE(1) ERR_CODE(0) FRAME_CAP(S) BEARER_CAP(DA) [|pptp]
09:36:42.815451 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [.], ack 157, win 108, options [nop,nop,TS val 629867 ecr 102184050], length 0
09:36:43.781507 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [P.], seq 157:325, ack 157, win 108, options [nop,nop,TS val 630109 ecr 102184050], length 168: pptp CTRL_MSGTYPE=OCRQ CALL_ID(0) CALL_SER_NUM(0) MIN_BPS(2400) MAX_BPS(10000000) [|pptp]
09:36:43.811849 IP my.dyndns.org.1723 > nb.firma.de.54686: Flags [P.], seq 157:189, ack 325, win 65211, options [nop,nop,TS val 102184060 ecr 630109], length 32: pptp CTRL_MSGTYPE=OCRP CALL_ID(2989) PEER_CALL_ID(0) RESULT_CODE(1) ERR_CODE(0) CAUSE_CODE(0) CONN_SPEED(14808325) [|pptp]
09:36:43.811900 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [.], ack 189, win 108, options [nop,nop,TS val 630116 ecr 102184060], length 0
09:36:43.812266 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 1, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:43.845329 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 0, ack 1, length 76: LCP, Conf-Request (0x01), id 0, length 58
09:36:43.845655 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 1, length 36: LCP, Conf-Ack (0x02), id 1, length 22
09:36:45.837106 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 2, length 72: LCP, Conf-Request (0x01), id 1, length 58
09:36:46.749688 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 2, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:46.776008 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 3, ack 2, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:36:48.838208 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 4, length 72: LCP, Conf-Request (0x01), id 2, length 58
09:36:49.754140 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 3, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:49.779966 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 5, ack 3, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:36:52.758135 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 4, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:52.784509 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 6, ack 4, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:36:52.834507 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 7, length 72: LCP, Conf-Request (0x01), id 3, length 58
09:36:55.762138 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 5, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:55.787263 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 8, ack 5, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:36:56.834130 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 9, length 72: LCP, Conf-Request (0x01), id 4, length 58
09:36:58.762142 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 6, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:36:58.785378 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 10, ack 6, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:37:00.839964 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 11, length 72: LCP, Conf-Request (0x01), id 5, length 58
09:37:01.766145 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 7, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:37:01.792891 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 12, ack 7, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:37:04.766148 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 8, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:37:04.789477 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 13, ack 8, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:37:04.836710 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 14, length 72: LCP, Conf-Request (0x01), id 6, length 58
09:37:07.770129 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 9, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:37:07.796836 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 15, ack 9, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:37:08.830279 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 16, length 72: LCP, Conf-Request (0x01), id 7, length 58
09:37:10.770132 IP nb.firma.de > my.dyndns.org: GREv1, call 2989, seq 10, length 36: LCP, Conf-Request (0x01), id 1, length 22
09:37:10.797311 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 17, ack 10, length 40: LCP, Conf-Ack (0x02), id 1, length 22
09:37:12.829923 IP my.dyndns.org > nb.firma.de: GREv1, call 61025, seq 18, length 72: LCP, Conf-Request (0x01), id 8, length 58
09:37:13.794446 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [P.], seq 325:341, ack 189, win 108, options [nop,nop,TS val 637612 ecr 102184060], length 16: pptp CTRL_MSGTYPE=CCRQ CALL_ID(0)
09:37:13.794590 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [F.], seq 341, ack 189, win 108, options [nop,nop,TS val 637612 ecr 102184060], length 0
09:37:13.825637 IP my.dyndns.org.1723 > nb.firma.de.54686: Flags [P.], seq 189:337, ack 341, win 65195, options [nop,nop,TS val 102184360 ecr 637612], length 148: pptp CTRL_MSGTYPE=CDN CALL_ID(2989) RESULT_CODE(0) ERR_CODE(0) CAUSE_CODE(0) [|pptp]
09:37:13.825687 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [R], seq 113062000, win 0, length 0
09:37:13.830436 IP my.dyndns.org.1723 > nb.firma.de.54686: Flags [F.], seq 337, ack 342, win 65195, options [nop,nop,TS val 102184360 ecr 637612], length 0
09:37:13.830459 IP nb.firma.de.54686 > my.dyndns.org.1723: Flags [R], seq 113062001, win 0, length 0

```

Any Idea?

Thomas

---

### Post by Lars Noodén on 2009-11-06
Notice the two categories...

[http://www.vpnc.org/vpn-standards.html](http://www.vpnc.org/vpn-standards.html)

---

### Post by aLiEnTxC on 2009-11-06
sorry, but I don't understand what you want to say?

Should I read now all RFCs to understand my problem?

It looks like, the client cant get the gre answer packets... I added the debug options and see exactly what is de-scripted there: [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#client_no_gre_rx](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#client_no_gre_rx)

but in tcpdump I can see the answer..?!

iptables is not configured -> so all default policys are on ACCEPT

---

