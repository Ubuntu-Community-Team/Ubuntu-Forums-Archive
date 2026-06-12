---
title: "Error connecting to PPTP VPN"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by murkle on 2010-09-07
Hi,

Having problems connecting to a work's VPN server.

syslog output pasted here:


```
Sep  7 22:45:31 localhost NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Sep  7 22:45:31 localhost NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1771
Sep  7 22:45:31 localhost NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep  7 22:45:31 localhost NetworkManager: <info>  VPN plugin state changed: 1
Sep  7 22:45:35 localhost NetworkManager: <info>  VPN plugin state changed: 3
Sep  7 22:45:35 localhost NetworkManager: <info>  VPN connection 'Brantas2' (Connect) reply received.
Sep  7 22:45:35 localhost pppd[1774]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep  7 22:45:35 localhost pppd[1774]: pppd 2.4.5 started by root, uid 0
Sep  7 22:45:35 localhost pppd[1774]: using channel 1
Sep  7 22:45:35 localhost NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep  7 22:45:35 localhost NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep  7 22:45:35 localhost pppd[1774]: Using interface ppp0
Sep  7 22:45:35 localhost pppd[1774]: Connect: ppp0 <--> /dev/pts/1
Sep  7 22:45:35 localhost pptp[1779]: nm-pptp-service-1771 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep  7 22:45:36 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Sep  7 22:45:36 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Sep  7 22:45:36 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Sep  7 22:45:36 localhost pppd[1774]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x29d3b026> <pcomp> <accomp>]
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 413).
Sep  7 22:45:37 localhost pppd[1774]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x6bbe54ff> <pcomp> <accomp>]
Sep  7 22:45:37 localhost pppd[1774]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x6bbe54ff> <pcomp> <accomp>]
Sep  7 22:45:37 localhost pppd[1774]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x29d3b026> <pcomp> <accomp>]
Sep  7 22:45:37 localhost pppd[1774]: rcvd [LCP EchoReq id=0x0 magic=0x6bbe54ff]
Sep  7 22:45:37 localhost pppd[1774]: sent [LCP EchoRep id=0x0 magic=0x29d3b026]
Sep  7 22:45:37 localhost pppd[1774]: rcvd [CHAP Challenge id=0x1 <433ba5d05c7934f0afb86355dfd98439>, name = "Draytek"]
Sep  7 22:45:37 localhost pppd[1774]: sent [CHAP Response id=0x1 <9d8f5860c73aea7a96060c18fddb4e020000000000000000a575eef3a52aa74733d620da780fcaca1c8dc944db0b050c00>, name = "alasdair.campbell"]
Sep  7 22:45:37 localhost pppd[1774]: rcvd [CHAP Success id=0x1 "\001S=AA4CDB08A2EEF7DD2BC37CBB7B489C76644C2A7F"]
Sep  7 22:45:37 localhost pppd[1774]: MS-CHAPv2 Success packet is badly formed.
Sep  7 22:45:37 localhost pppd[1774]: CHAP authentication failed
Sep  7 22:45:37 localhost pppd[1774]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
Sep  7 22:45:37 localhost pppd[1774]: rcvd [IPCP ConfReq id=0x1 <addr 192.168.1.254> <compress VJ 0f 01>]
Sep  7 22:45:37 localhost pppd[1774]: Discarded non-LCP packet when LCP not open
Sep  7 22:45:37 localhost pppd[1774]: rcvd [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
Sep  7 22:45:37 localhost pppd[1774]: Discarded non-LCP packet when LCP not open
Sep  7 22:45:37 localhost pppd[1774]: rcvd [LCP TermAck id=0x2]
Sep  7 22:45:37 localhost pppd[1774]: Connection terminated.
Sep  7 22:45:37 localhost NetworkManager: <info>  VPN plugin failed: 1
Sep  7 22:45:37 localhost NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep  7 22:45:37 localhost pppd[1774]: Waiting for 1 child processes...
Sep  7 22:45:37 localhost pppd[1774]:   script /usr/sbin/pptp brantas.myvnc.com --nolaunchpppd --logstring nm-pptp-service-1771, pid 1776
Sep  7 22:45:37 localhost pptp[1779]: nm-pptp-service-1771 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Sep  7 22:45:37 localhost pptp[1779]: nm-pptp-service-1771 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Sep  7 22:45:37 localhost pptp[1787]: nm-pptp-service-1771 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Sep  7 22:45:37 localhost NetworkManager: <info>  VPN plugin failed: 1
Sep  7 22:45:37 localhost pppd[1774]: Script /usr/sbin/pptp brantas.myvnc.com --nolaunchpppd --logstring nm-pptp-service-1771 finished (pid 1776), status = 0x0
Sep  7 22:45:37 localhost pppd[1774]: Exit.
Sep  7 22:45:37 localhost NetworkManager: <info>  VPN plugin state changed: 6
Sep  7 22:45:37 localhost NetworkManager: <info>  VPN plugin state change reason: 0
Sep  7 22:45:37 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep  7 22:45:37 localhost NetworkManager: <info>  Policy set 'Auto Brantas' (wlan0) as default for routing and DNS.
Sep  7 22:45:42 localhost AptDaemon: INFO: Initializing daemon
Sep  7 22:45:50 localhost NetworkManager: <debug> [1283895950.003135] ensure_killed(): waiting for vpn service pid 1771 to exit
Sep  7 22:45:50 localhost NetworkManager: <debug> [1283895950.003375] ensure_killed(): vpn service pid 1771 cleaned up

```

One of the major things sticking out to me is this:
```
Sep  7 22:45:37 localhost pppd[1774]: MS-CHAPv2 Success packet is badly formed.
```


Any suggestions greatly appreciated

---

### Post by lk47 on 2011-01-24
Hi,

> **murkle said:**
> 
```

Sep  7 22:45:37 localhost pppd[1774]: rcvd [CHAP Success id=0x1 "\001S=AA4CDB08A2EEF7DD2BC37CBB7B489C76644C2A7F"]
Sep  7 22:45:37 localhost pppd[1774]: MS-CHAPv2 Success packet is badly formed.

```


I am having similar issues connecting to a draytek server. It seems their MS-CHAPv2 implementation is buggy...

I managed to connect only after recompiling pppd code to "eat" the extra characters.

I'm not an ubuntu user but I should be able to help you out if you still need to

---

### Post by murkle on 2011-04-24
> **lk47 said:**
> Hi,



I am having similar issues connecting to a draytek server. It seems their MS-CHAPv2 implementation is buggy...

I managed to connect only after recompiling pppd code to "eat" the extra characters.

I'm not an ubuntu user but I should be able to help you out if you still need to

Gah I never got email notification of this reply must have forgotten to enable this. I would love a pointer on to how to fix this.. it's the only thing keeping a copy of XP running on my laptop :(

---

### Post by rowanp01 on 2011-11-29
Did you get a response for this? I am having the same problem and am looking for a patch for the client. I guess I could look at writing one myself, but would be much easier if someone has already done the work.

---

### Post by murkle on 2011-11-29
> **rowanp01 said:**
> Did you get a response for this? I am having the same problem and am looking for a patch for the client. I guess I could look at writing one myself, but would be much easier if someone has already done the work.

I found a thread on here somewhere with instructions on recompiling pppd and eating those extra characters. I did all that, and VPN still failed to connect. I haven't tried in months though, has to be said.

Let me know if you get any further with this

---

### Post by NexusStar on 2011-11-30
I've too have problem connecting to pptp vpn from Ubuntu I personal y don't know if my problem are similar to yours but if someone found a solution it will be good to point it out.

---

