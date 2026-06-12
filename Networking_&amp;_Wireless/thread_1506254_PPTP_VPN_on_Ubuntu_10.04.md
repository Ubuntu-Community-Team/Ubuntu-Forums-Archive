---
title: "PPTP VPN on Ubuntu 10.04"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by James2k on 2010-06-10
My college has a VPN server setup that allows students to access certain network drives, the college network is running on Windows. I've been battling with setting up a VPN connection for a while but I feel I am close to getting a successful connection.

Previously I got that VPN service failed to start error, but have managed to overcome that error, however I know get an even less informative error of "The VPN connection failed". I have tried every setting I've read on guides and nothing seems to work. Here's a log of an attempted VPN connection:

> 
Jun 10 10:28:54 james-compaq NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jun 10 10:28:54 james-compaq NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2531
Jun 10 10:28:54 james-compaq NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jun 10 10:28:54 james-compaq NetworkManager: <info>  VPN plugin state changed: 1
Jun 10 10:28:59 james-compaq NetworkManager: <info>  VPN plugin state changed: 3
Jun 10 10:28:59 james-compaq NetworkManager: <info>  VPN connection 'SNC VPN' (Connect) reply received.
Jun 10 10:28:59 james-compaq pppd[2534]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun 10 10:28:59 james-compaq pppd[2534]: pppd 2.4.5 started by root, uid 0
Jun 10 10:28:59 james-compaq NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 10 10:28:59 james-compaq NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 10 10:28:59 james-compaq pppd[2534]: Using interface ppp0
Jun 10 10:28:59 james-compaq pppd[2534]: Connect: ppp0 <--> /dev/pts/0
Jun 10 10:28:59 james-compaq pptp[2538]: nm-pptp-service-2531 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun 10 10:29:20 james-compaq pptp[2540]: nm-pptp-service-2531 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
Jun 10 10:29:20 james-compaq pptp[2540]: nm-pptp-service-2531 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 194.83.198.248
Jun 10 10:29:20 james-compaq pptp[2538]: nm-pptp-service-2531 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Jun 10 10:29:20 james-compaq pppd[2534]: Modem hangup
Jun 10 10:29:20 james-compaq pppd[2534]: Connection terminated.
Jun 10 10:29:20 james-compaq NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 10 10:29:20 james-compaq NetworkManager: <info>  VPN plugin failed: 1
Jun 10 10:29:20 james-compaq pppd[2534]: Exit.
Jun 10 10:29:20 james-compaq NetworkManager: <info>  VPN plugin failed: 1
Jun 10 10:29:20 james-compaq NetworkManager: <info>  VPN plugin failed: 1
Jun 10 10:29:20 james-compaq NetworkManager: <info>  VPN plugin state changed: 6
Jun 10 10:29:20 james-compaq NetworkManager: <info>  VPN plugin state change reason: 0
Jun 10 10:29:20 james-compaq NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jun 10 10:29:20 james-compaq NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jun 10 10:29:33 james-compaq NetworkManager: <debug> [1276162173.001879] ensure_killed(): waiting for vpn service pid 2531 to exit
Jun 10 10:29:33 james-compaq NetworkManager: <debug> [1276162173.002079] ensure_killed(): vpn service pid 2531 cleaned up


It seems that a connection is initially successful but then it times out after a short time.

Any help on this would be greatly received! 

Thanks,

James

---

### Post by aggiemarine07 on 2010-06-18
i am having the same issues. i never had a problem with ciscovpn or openvpn. why is is so difficult with pptp? 

also if anyone can provide a solution on how to fix this in 10.04 (of which there is none just 9.10 and earlier), then it would be greatly appreciated. Thanks.

---

### Post by travisc94 on 2010-07-09
I had the same issue until I changed some of the authentication and encryption settings. 

In the PPTP server settings, make sure you allow the types of encryption and/or authentication the client can deal with. I use webmin to edit my PPTP server settings, so it was easier to recognize the problem.

---

### Post by technoboi on 2010-11-22
The 'Failed to start' issue can be solved by unchecking the 'Available to all users' box in the GUI. :)
..but then I get 'Failed to connect'.
:(

---

### Post by sinukas on 2011-02-18
[bump] I'm having the same problem above and can't seem to get it resolved. below is my syslog:

```
Feb 18 15:58:02 gold NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Feb 18 15:58:02 gold NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 9433 
Feb 18 15:58:02 gold NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Feb 18 15:58:02 gold NetworkManager: <info>  VPN plugin state changed: 1 
Feb 18 15:58:02 gold NetworkManager: <info>  VPN plugin state changed: 3 
Feb 18 15:58:02 gold NetworkManager: <info>  VPN connection 'ITSO' (Connect) reply received. 
Feb 18 15:58:02 gold pppd[9435]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Feb 18 15:58:02 gold pppd[9435]: pppd options in effect:
Feb 18 15:58:02 gold pppd[9435]: debug^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: nodetach^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: dump^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: noauth^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: user will^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: ^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: pty /usr/sbin/pptp ****************** --nolaunchpppd --logstring nm-pptp-service-9433^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: crtscts^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: ^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: asyncmap 0^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: lcp-echo-failure 0^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: lcp-echo-interval 0^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: hide-password^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: novj^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: ipparam nm-pptp-service-9433^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: noipdefault^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: nodefaultroute^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: proxyarp^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: usepeerdns^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: nobsdcomp^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: nodeflate^I^I# (from command line)
Feb 18 15:58:02 gold pppd[9435]: noipx^I^I# (from /etc/ppp/options)
Feb 18 15:58:02 gold pppd[9435]: pppd 2.4.5 started by root, uid 0
Feb 18 15:58:02 gold pppd[9435]: using channel 26
Feb 18 15:58:02 gold NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 18 15:58:02 gold NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb 18 15:58:02 gold pppd[9435]: Using interface ppp0
Feb 18 15:58:02 gold pppd[9435]: Connect: ppp0 <--> /dev/pts/2
Feb 18 15:58:02 gold pptp[9438]: nm-pptp-service-9433 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Feb 18 15:58:02 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Feb 18 15:58:02 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Feb 18 15:58:02 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Feb 18 15:58:03 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:03 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Feb 18 15:58:03 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Feb 18 15:58:03 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 5121). 
Feb 18 15:58:06 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:09 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:12 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:15 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:18 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:21 gold pppd[9435]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9341589> <pcomp> <accomp>]
Feb 18 15:58:23 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_disp:pptp_ctrl.c:788]: Received Stop Control Connection Request.
Feb 18 15:58:23 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply' 
Feb 18 15:58:23 gold pptp[9446]: nm-pptp-service-9433 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Feb 18 15:58:23 gold pptp[9446]: nm-pptp-service-9433 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Feb 18 15:58:23 gold pptp[9446]: nm-pptp-service-9433 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Feb 18 15:58:23 gold pppd[9435]: Script /usr/sbin/pptp ************** --nolaunchpppd --logstring nm-pptp-service-9433 finished (pid 9437), status = 0x0
Feb 18 15:58:23 gold pppd[9435]: Modem hangup
Feb 18 15:58:23 gold pppd[9435]: Connection terminated.
Feb 18 15:58:23 gold NetworkManager: <info>  VPN plugin failed: 1 
Feb 18 15:58:23 gold NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 18 15:58:23 gold pppd[9435]: Exit.
Feb 18 15:58:23 gold NetworkManager: <info>  VPN plugin failed: 1 
Feb 18 15:58:23 gold NetworkManager: <info>  VPN plugin failed: 1 
Feb 18 15:58:23 gold NetworkManager: <info>  VPN plugin state changed: 6 
Feb 18 15:58:23 gold NetworkManager: <info>  VPN plugin state change reason: 0 
Feb 18 15:58:23 gold NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Feb 18 15:58:23 gold NetworkManager: <info>  Policy set 'VT GigE' (eth0) as default for routing and DNS. 
Feb 18 15:58:36 gold NetworkManager: <debug> [1298062716.002850] ensure_killed(): waiting for vpn service pid 9433 to exit 
Feb 18 15:58:36 gold NetworkManager: <debug> [1298062716.002952] ensure_killed(): vpn service pid 9433 cleaned up 

```

---

### Post by 2devnull on 2011-03-25
I'm hoping to get some help here with 10.04 and PPTP. I get the error below. I tried using the built in applet and setting up from the command line, but still can't get connected. 

I changed the IP and names below to something random since this is a public forum.


```
#:/etc/ppp/ip-up.d$ sudo pon MYCONN
using channel 9
Using interface ppp0
Connect: ppp0 <--> /dev/pts/3
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9af690a3> <pcomp> <accomp>]
anon warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
anon fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 102.155.11.1
anon fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Modem hangup
Connection terminated.
Script pptp vpnserver.domain.com --nolaunchpppd finished (pid 15532), status = 0x1

```

---

### Post by saeed144 on 2011-08-02
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

