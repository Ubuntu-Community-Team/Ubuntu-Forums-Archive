---
title: "Conecting to VPN"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by NexusStar on 2011-11-26
Hi to all, first I am new to Ubunto so be kind.
I've got the following problem at home I have two separate machines one which runs Windows XP 64 bit and one that runs Ubuntu (11.10).
On windows machine I could connect to VPN (PPTP) without problem but
when I try to connect from Ubunto using network manager with same settings as on Windows it fails with Failed to connect message
I try also to connect through command line using instructions from Ubuntu Wiki but the result was the same
[FONT=monospace]LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
[/FONT]
So what could be the problem and where to look for solution?

---

### Post by NexusStar on 2011-11-30
Anyone has solution for that it drives me crazy and I could not use Ubuntu from home to work with files at work 
Plz someone

---

### Post by dragos_iliescu_2005 on 2011-11-30
In the Network Manager > VPN,
check the option <<Disable DeadPeer Detection>>.

Hope to help.

---

### Post by NexusStar on 2011-11-30
I see this option only on vpnc connection. Is there similar option for pptp which I can not find?

---

### Post by NexusStar on 2011-11-30
And here is some extract from syslog if someone can make anything from it


```
Nov 30 22:23:58 <> NetworkManager[775]: <info> Starting VPN service 'pptp'...
Nov 30 22:23:58 <> NetworkManager[775]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 4484
Nov 30 22:23:58 <> NetworkManager[775]: <info> VPN service 'pptp' appeared; activating connections
Nov 30 22:23:58 <> NetworkManager[775]: <info> VPN plugin state changed: 1
Nov 30 22:24:09 <> NetworkManager[775]: <info> VPN plugin state changed: 3
Nov 30 22:24:09 <> NetworkManager[775]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Nov 30 22:24:10 <> pppd[4488]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Nov 30 22:24:10 <> pppd[4488]: pppd 2.4.5 started by root, uid 0
Nov 30 22:24:10 <> pptp[4491]: nm-pptp-service-4484 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov 30 22:24:10 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov 30 22:24:10 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov 30 22:24:10 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov 30 22:24:10 <> pppd[4488]: Using interface ppp0
Nov 30 22:24:10 <> pppd[4488]: Connect: ppp0 <--> /dev/pts/0
Nov 30 22:24:10 <> NetworkManager[775]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 30 22:24:10 <> NetworkManager[775]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 30 22:24:11 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov 30 22:24:11 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov 30 22:24:11 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 8192).
Nov 30 22:24:41 <> pptp[4499]: nm-pptp-service-4484 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Nov 30 22:24:41 <> pptp[4499]: nm-pptp-service-4484 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Nov 30 22:24:41 <> pptp[4499]: nm-pptp-service-4484 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov 30 22:24:41 <> pppd[4488]: Modem hangup
Nov 30 22:24:41 <> NetworkManager[775]: <warn> VPN plugin failed: 1
Nov 30 22:24:41 <> pppd[4488]: Connection terminated.
```

---

### Post by nm_geo on 2011-11-30
You might try setting up your CHAPS like the screenshot below.

---

### Post by sammiev on 2011-11-30
Running a vpn by pptp wouldn't CHAPS be required? I never tried it any other way.

---

### Post by NexusStar on 2011-12-01
> **nm_geo said:**
> You might try setting up your CHAPS like the screenshot below.
Thank you for sharing this screen shot but I try every possible setting configuration at network manager and nothing The frustrating thing is that my windows machine connects without problem and it and Ubunto one reside in the same LAN (at my home) and use the same settings.

---

### Post by NexusStar on 2011-12-03
I narrow the culprit for the problem it appears to be combination between Ubunto and my router (Canyon CN-WF514 - quite old bugger):o so now it's to determine what is not working?
Any suggestions are highly welcome

---

### Post by NexusStar on 2011-12-09
I still battle with this one :(
So will provide some more information if someone could point to  some solution for this problem. 
I've got another point from where I could connect which is from another router Linksys WRT54GL there I could connect without problem
here is the log from successful connection from there:
```
Dec 10 02:23:28 ub NetworkManager[502]: <info> Starting VPN service 'pptp'...
Dec 10 02:23:28 ub NetworkManager[502]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 24545
Dec 10 02:23:28 ub NetworkManager[502]: <info> VPN service 'pptp' appeared; activating connections
Dec 10 02:23:28 ub NetworkManager[502]: <info> VPN plugin state changed: 1
Dec 10 02:23:29 ub NetworkManager[502]: <info> VPN plugin state changed: 3
Dec 10 02:23:29 ub NetworkManager[502]: <info> VPN connection 'APRA' (Connect) reply received.
Dec 10 02:23:29 ub pppd[24547]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Dec 10 02:23:29 ub pppd[24547]: pppd 2.4.5 started by root, uid 0
Dec 10 02:23:29 ub NetworkManager[502]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 02:23:29 ub NetworkManager[502]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 10 02:23:29 ub pppd[24547]: Using interface ppp0
Dec 10 02:23:29 ub pppd[24547]: Connect: ppp0 <--> /dev/pts/1
Dec 10 02:23:29 ub pptp[24550]: nm-pptp-service-24545 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 10 02:23:29 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 10 02:23:29 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 10 02:23:29 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 10 02:23:30 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 10 02:23:30 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 10 02:23:30 ub pptp[24558]: nm-pptp-service-24545 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 17408).
Dec 10 02:23:30 ub pppd[24547]: CHAP authentication succeeded
Dec 10 02:23:31 ub kernel: [115146.278694] PPP MPPE Compression module registered
Dec 10 02:23:31 ub pppd[24547]: MPPE 128-bit stateless compression enabled
```

And when connected to the other router without changing settings or machine 
```


Dec 10 02:31:25 ub NetworkManager[502]: <info> Starting VPN service 'pptp'...
Dec 10 02:31:25 ub NetworkManager[502]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 24995
Dec 10 02:31:25 ub NetworkManager[502]: <info> VPN service 'pptp' appeared; activating connections
Dec 10 02:31:25 ub NetworkManager[502]: <info> VPN plugin state changed: 1
Dec 10 02:31:25 ub NetworkManager[502]: <info> VPN plugin state changed: 3
Dec 10 02:31:25 ub NetworkManager[502]: <info> VPN connection 'APRA' (Connect) reply received.
Dec 10 02:31:25 ub pppd[24997]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Dec 10 02:31:26 ub pppd[24997]: pppd 2.4.5 started by root, uid 0
Dec 10 02:31:26 ub NetworkManager[502]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 02:31:26 ub NetworkManager[502]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 10 02:31:26 ub pppd[24997]: Using interface ppp0
Dec 10 02:31:26 ub pppd[24997]: Connect: ppp0 <--> /dev/pts/1
Dec 10 02:31:26 ub pptp[25000]: nm-pptp-service-24995 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 10 02:31:26 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 10 02:31:26 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 10 02:31:26 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 10 02:31:26 ub ntpdate[24977]: adjust time server 91.189.94.4 offset 0.027897 sec
Dec 10 02:31:27 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 10 02:31:27 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 10 02:31:27 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 17536).
Dec 10 02:31:43 ub kernel: [115638.894775] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Dec 10 02:31:57 ub pppd[24997]: LCP: timeout sending Config-Requests
Dec 10 02:31:57 ub pppd[24997]: Connection terminated.
Dec 10 02:31:57 ub avahi-daemon[504]: Withdrawing workstation service for ppp0.
Dec 10 02:31:57 ub NetworkManager[502]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 10 02:31:57 ub pppd[24997]: Modem hangup
Dec 10 02:31:57 ub pptp[25000]: nm-pptp-service-24995 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 10 02:31:57 ub pptp[25000]: nm-pptp-service-24995 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 10 02:31:57 ub NetworkManager[502]: <warn> VPN plugin failed: 1
Dec 10 02:31:57 ub pppd[24997]: Exit.
Dec 10 02:31:57 ub pptp[25008]: nm-pptp-service-24995 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 10 02:31:57 ub pptp[25008]: nm-pptp-service-24995 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Dec 10 02:31:57 ub pptp[25008]: nm-pptp-service-24995 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 10 02:31:57 ub NetworkManager[502]: <warn> VPN plugin failed: 1
Dec 10 02:31:57 ub NetworkManager[502]: <info> VPN plugin state changed: 6
Dec 10 02:31:57 ub NetworkManager[502]: <info> VPN plugin state change reason: 0
Dec 10 02:31:57 ub NetworkManager[502]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 10 02:31:57 ub NetworkManager[502]: <info> Policy set 'Auto Nikol' (wlan0) as default for IPv4 routing and DNS.
Dec 10 02:32:02 ub NetworkManager[502]: <info> VPN service 'pptp' disappeared

```

---

### Post by NexusStar on 2011-12-26
at the end I changed my old canyon router with new one and now I can connect without problems but still if someone could look up the logs and tell me what was the problem with the old router

---

