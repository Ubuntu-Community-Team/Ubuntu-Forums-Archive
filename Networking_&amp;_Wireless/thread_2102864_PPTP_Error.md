---
title: "PPTP Error"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by Hexno on 2013-01-08
I try multiple configurations with this connection and I keep getting a failed response. We know the VPN username/pass is good because we were able to use a Windows and Mac to connect to it. I'm not sure why I keep getting disconnected from this VPN.

```
Jan  8 10:43:16 ubuntu NetworkManager[892]: <info> Starting VPN service 'pptp'...
Jan  8 10:43:16 ubuntu NetworkManager[892]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 9145
Jan  8 10:43:16 ubuntu NetworkManager[892]: <info> VPN service 'pptp' appeared; activating connections
Jan  8 10:43:16 ubuntu NetworkManager[892]: <info> VPN plugin state changed: starting (3)
Jan  8 10:43:16 ubuntu pppd[9149]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan  8 10:43:16 ubuntu NetworkManager[892]: <info> VPN connection 'VPN connection 1' (Connect) reply received.
Jan  8 10:43:16 ubuntu pppd[9149]: pppd 2.4.5 started by root, uid 0
Jan  8 10:43:16 ubuntu pppd[9149]: Using interface ppp0
Jan  8 10:43:16 ubuntu pppd[9149]: Connect: ppp0 <--> /dev/pts/3
Jan  8 10:43:16 ubuntu pptp[9152]: nm-pptp-service-9145 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  8 10:43:16 ubuntu NetworkManager[892]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 10:43:16 ubuntu NetworkManager[892]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  8 10:43:16 ubuntu NetworkManager[892]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan  8 10:43:16 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  8 10:43:16 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  8 10:43:16 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 14569).
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jan  8 10:43:17 ubuntu pppd[9149]: LCP terminated by peer (&^WCS^@<M-Mt^@^@^BM-3)
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jan  8 10:43:17 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jan  8 10:43:20 ubuntu pppd[9149]: Connection terminated.
Jan  8 10:43:20 ubuntu NetworkManager[892]: <warn> VPN plugin failed: 1
Jan  8 10:43:20 ubuntu NetworkManager[892]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 10:43:20 ubuntu pppd[9149]: Modem hangup
Jan  8 10:43:20 ubuntu pptp[9152]: nm-pptp-service-9145 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan  8 10:43:20 ubuntu pptp[9152]: nm-pptp-service-9145 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan  8 10:43:20 ubuntu pptp[9160]: nm-pptp-service-9145 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan  8 10:43:20 ubuntu NetworkManager[892]: <warn> VPN plugin failed: 1
Jan  8 10:43:20 ubuntu pppd[9149]: Exit.
Jan  8 10:43:20 ubuntu pptp[9160]: nm-pptp-service-9145 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  8 10:43:20 ubuntu pptp[9160]: nm-pptp-service-9145 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  8 10:43:20 ubuntu NetworkManager[892]: <warn> VPN plugin failed: 1
Jan  8 10:43:20 ubuntu NetworkManager[892]: <info> VPN plugin state changed: stopped (6)
Jan  8 10:43:20 ubuntu NetworkManager[892]: <info> VPN plugin state change reason: 0
Jan  8 10:43:20 ubuntu NetworkManager[892]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan  8 10:43:20 ubuntu NetworkManager[892]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan  8 10:43:26 ubuntu NetworkManager[892]: <info> VPN service 'pptp' disappeared

```

---

### Post by jonobr on 2013-01-08
Hello


I had this before and it was fixed by lowering the MTU size ,
mind you that was on 10.04 
You can find your current mtu setting by opening a terminal and typing ifconfig and look for mtu (usually 1500)

you can change it temporarily to test it by using (off the top of my head)

```
sudo ifconfig eth0 mtu 1492
```
(I'm assuming your using an Ethernet interface)

You could try lower.
After you restart it will reset to default.

---

### Post by Hexno on 2013-01-09
Tried lowering the MTU to 1000, I'm still getting the same error. :-/

```
Jan  9 08:30:40 ubuntu NetworkManager[883]: <info> Starting VPN service 'pptp'...
Jan  9 08:30:40 ubuntu NetworkManager[883]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 3452
Jan  9 08:30:40 ubuntu NetworkManager[883]: <info> VPN service 'pptp' appeared; activating connections
Jan  9 08:30:43 ubuntu NetworkManager[883]: <info> VPN plugin state changed: starting (3)
Jan  9 08:30:43 ubuntu NetworkManager[883]: <info> VPN connection 'acus pptp' (Connect) reply received.
Jan  9 08:30:43 ubuntu pppd[3461]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan  9 08:30:43 ubuntu pppd[3461]: pppd 2.4.5 started by root, uid 0
Jan  9 08:30:43 ubuntu pptp[3466]: nm-pptp-service-3452 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan  9 08:30:43 ubuntu pppd[3461]: Using interface ppp0
Jan  9 08:30:43 ubuntu pppd[3461]: Connect: ppp0 <--> /dev/pts/0
Jan  9 08:30:43 ubuntu NetworkManager[883]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  9 08:30:43 ubuntu NetworkManager[883]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  9 08:30:43 ubuntu NetworkManager[883]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan  9 08:30:43 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan  9 08:30:43 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan  9 08:30:43 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 61279).
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jan  9 08:30:44 ubuntu pppd[3461]: LCP terminated by peer (vM-wpM- ^@<M-Mt^@^@^BM-3)
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Jan  9 08:30:44 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Jan  9 08:30:46 ubuntu tpvmlpd2[3476]: readlink("/dev/vmwcomgw") failed with 2
Jan  9 08:30:47 ubuntu pppd[3461]: Connection terminated.
Jan  9 08:30:47 ubuntu avahi-daemon[610]: Withdrawing workstation service for ppp0.
Jan  9 08:30:47 ubuntu NetworkManager[883]: <warn> VPN plugin failed: 1
Jan  9 08:30:47 ubuntu NetworkManager[883]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  9 08:30:47 ubuntu pptp[3466]: nm-pptp-service-3452 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan  9 08:30:47 ubuntu pppd[3461]: Modem hangup
Jan  9 08:30:47 ubuntu pptp[3466]: nm-pptp-service-3452 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan  9 08:30:47 ubuntu pptp[3475]: nm-pptp-service-3452 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan  9 08:30:47 ubuntu pptp[3475]: nm-pptp-service-3452 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan  9 08:30:47 ubuntu NetworkManager[883]: <warn> VPN plugin failed: 1
Jan  9 08:30:47 ubuntu pptp[3475]: nm-pptp-service-3452 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan  9 08:30:47 ubuntu pppd[3461]: Exit.
Jan  9 08:30:47 ubuntu NetworkManager[883]: <warn> VPN plugin failed: 1
Jan  9 08:30:47 ubuntu NetworkManager[883]: <info> VPN plugin state changed: stopped (6)
Jan  9 08:30:47 ubuntu NetworkManager[883]: <info> VPN plugin state change reason: 0
Jan  9 08:30:47 ubuntu NetworkManager[883]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan  9 08:30:47 ubuntu NetworkManager[883]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan  9 08:30:52 ubuntu NetworkManager[883]: <info> VPN service 'pptp' disappeared

```

---

### Post by dpurgert on 2013-01-09
quick google search turned up this thread.  Not sure if it'll help in this case though... [http://ubuntuforums.org/showthread.php?p=7002673](http://ubuntuforums.org/showthread.php?p=7002673)

---

