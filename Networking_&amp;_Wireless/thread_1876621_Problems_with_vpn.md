---
title: "Problems with vpn"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by Friwise on 2011-11-06
Hi!!!
Another problem that I just found out today.
I am using vpn in order to use some services of my university.
I had one vpn connection that was properly working on 11.04 and after I installed 11.10 I only today tried to connect to it.
Unfortunately it cannot connect.
Do you have any idea what shall I do?

Thanks in advance

---

### Post by Friwise on 2011-11-06
Last Monday we have chenged internet service and, consequently, we have a new router at home. Personally, I am using wireless. Is it possible that the problem has any relation with that issue?

---

### Post by Friwise on 2011-11-11
Hello again!!!
With some help from another forum I used gnome-system-log and it gave me these results while trying to connect:

[B]```
&#967;&#967;&#967;-Inspiron-N5010 NetworkManager[978]: <info> Starting VPN service 'pptp'...
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 4389
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN service 'pptp' appeared; activating connections
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN plugin state changed: 1
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN plugin state changed: 3
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN connection 'Aigaio' (Connect) reply received.
Nov 11 15:10:47 xxx-Inspiron-N5010 pppd[4391]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Nov 11 15:10:47 xxx-Inspiron-N5010 pppd[4391]: pppd 2.4.5 started by root, uid 0
Nov 11 15:10:47 xxx-Inspiron-N5010 pppd[4391]: Using interface ppp0
Nov 11 15:10:47 xxx-Inspiron-N5010 pppd[4391]: Connect: ppp0 <--> /dev/pts/0
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 11 15:10:47 xxx-Inspiron-N5010 NetworkManager[978]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 11 15:10:47 xxx-Inspiron-N5010 pptp[4394]: nm-pptp-service-4389 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov 11 15:10:47 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov 11 15:10:47 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 11 15:10:47 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 11 15:10:48 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov 11 15:10:48 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 11 15:10:48 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 55786).
Nov 11 15:11:18 xxx-Inspiron-N5010 pppd[4391]: LCP: timeout sending Config-Requests
Nov 11 15:11:18 xxx-Inspiron-N5010 pppd[4391]: Connection terminated.
Nov 11 15:11:18 xxx-Inspiron-N5010 avahi-daemon[977]: Withdrawing workstation service for ppp0.
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <warn> VPN plugin failed: 1
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 11 15:11:18 xxx-Inspiron-N5010 pptp[4394]: nm-pptp-service-4389 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Nov 11 15:11:18 xxx-Inspiron-N5010 pptp[4394]: nm-pptp-service-4389 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Nov 11 15:11:18 xxx-Inspiron-N5010 pppd[4391]: Modem hangup
Nov 11 15:11:18 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Nov 11 15:11:18 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov 11 15:11:18 xxx-Inspiron-N5010 pptp[4402]: nm-pptp-service-4389 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov 11 15:11:18 xxx-Inspiron-N5010 pppd[4391]: Exit.
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <warn> VPN plugin failed: 1
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <warn> VPN plugin failed: 1
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN plugin state changed: 6
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN plugin state change reason: 0
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Nov 11 15:11:18 xxx-Inspiron-N5010 NetworkManager[978]: <info> Policy set 'CYTA xxx' (wlan0) as default for IPv4 routing and DNS.
Nov 11 15:11:23 xxx-Inspiron-N5010 NetworkManager[978]: <info> VPN service 'pptp' disappeared
Nov 11 15:13:30 xxx-Inspiron-N5010 kernel: [ 3009.750278] chromium-browse[4286]: segfault at 2166e968 ip 00007f031b557c08 sp 00007fff6239a110 error 4 in libX11.so.6.3.0[7f031b522000+133000] 
Nov 11 15:17:01 xxx-Inspiron-N5010 CRON[4578]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```[/B]

Do you have any suggestion?

---

