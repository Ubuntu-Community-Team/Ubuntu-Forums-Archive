---
title: "VPN Disconnects right after Authenticating"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by acidblue on 2010-11-08
I'm having the hardest time setting up a VPN server in 10.04.
I'm using the PPTP protocol.
I finally got my router to stop dropping GRE packets.
But I still cannot log into my server.
It seems to disconnect while waiting for IPCP config- requests, what ever they are.

Here is my syslog:


```
21:30:13 darkstar NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov  7 21:30:13 darkstar NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 10810
Nov  7 21:30:13 darkstar NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Nov  7 21:30:13 darkstar NetworkManager: <info>  VPN plugin state changed: 1
Nov  7 21:30:13 darkstar NetworkManager: <info>  VPN plugin state changed: 3
Nov  7 21:30:13 darkstar NetworkManager: <info>  VPN connection 'darkstar' (Connect) reply received.
Nov  7 21:30:13 darkstar pppd[10812]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov  7 21:30:13 darkstar pppd[10812]: pppd 2.4.5 started by root, uid 0
Nov  7 21:30:13 darkstar NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  7 21:30:13 darkstar NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov  7 21:30:13 darkstar pppd[10812]: Using interface ppp0
Nov  7 21:30:13 darkstar pppd[10812]: Connect: ppp0 <--> /dev/pts/3
Nov  7 21:30:14 darkstar pptp[10816]: nm-pptp-service-10810 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov  7 21:30:14 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Nov  7 21:30:14 darkstar pptpd[10824]: CTRL: Client 192.168.1.1 control connection started
Nov  7 21:30:14 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Nov  7 21:30:14 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Nov  7 21:30:15 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Nov  7 21:30:15 darkstar pptpd[10824]: CTRL: Starting call (launching pppd, opening GRE)
Nov  7 21:30:15 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Nov  7 21:30:15 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 128).
Nov  7 21:30:15 darkstar pppd[10826]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Nov  7 21:30:15 darkstar pppd[10826]: pppd 2.4.5 started by root, uid 0
Nov  7 21:30:15 darkstar pppd[10826]: Using interface ppp1
Nov  7 21:30:15 darkstar NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  7 21:30:15 darkstar NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  7 21:30:15 darkstar pppd[10826]: Connect: ppp1 <--> /dev/pts/4
Nov  7 21:30:15 darkstar pptpd[10824]: GRE: Bad checksum from pppd.
Nov  7 21:30:15 darkstar pppd[10812]: CHAP authentication succeeded
Nov  7 21:30:15 darkstar pppd[10826]: MPPE 128-bit stateless compression enabled
Nov  7 21:30:15 darkstar pppd[10812]: MPPE 128-bit stateless compression enabled
Nov  7 21:30:15 darkstar pppd[10826]: found interface wlan0 for proxy arp
Nov  7 21:30:15 darkstar pppd[10826]: local  IP address 192.168.0.1
Nov  7 21:30:15 darkstar pppd[10826]: remote IP address 192.168.1.1
Nov  7 21:30:45 darkstar pppd[10812]: **IPCP: timeout sending Config-Requests**
Nov  7 21:30:45 darkstar pppd[10812]: MPPE disabled
Nov  7 21:30:48 darkstar pppd[10812]: Connection terminated.
Nov  7 21:30:48 darkstar NetworkManager: <info>  VPN plugin failed: 1
Nov  7 21:30:48 darkstar NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  7 21:30:48 darkstar pppd[10812]: Modem hangup
Nov  7 21:30:48 darkstar pptp[10816]: nm-pptp-service-10810 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Nov  7 21:30:48 darkstar pptp[10816]: nm-pptp-service-10810 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Nov  7 21:30:48 darkstar pptp[10823]: nm-pptp-service-10810 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Nov  7 21:30:48 darkstar pptp[10823]: nm-pptp-service-10810 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Nov  7 21:30:48 darkstar pptp[10823]: nm-pptp-service-10810 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Nov  7 21:30:48 darkstar pppd[10812]: Exit.
Nov  7 21:30:48 darkstar NetworkManager: <info>  VPN plugin failed: 1
Nov  7 21:30:48 darkstar NetworkManager: <info>  VPN plugin failed: 1
Nov  7 21:30:48 darkstar NetworkManager: <info>  VPN plugin state changed: 6
Nov  7 21:30:48 darkstar NetworkManager: <info>  VPN plugin state change reason: 0
Nov  7 21:30:48 darkstar NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov  7 21:30:48 darkstar NetworkManager: <info>  Policy set 'Auto dd-wrt' (wlan0) as default for routing and DNS.
Nov  7 21:31:01 darkstar NetworkManager: <debug> [1289194261.000773] ensure_killed(): waiting for vpn service pid 10810 to exit
Nov  7 21:31:01 darkstar NetworkManager: <debug> [1289194261.000929] ensure_killed(): vpn service pid 10810 cleaned up
Nov  7 21:32:45 darkstar pppd[10826]: No response to 4 echo-requests
Nov  7 21:32:45 darkstar pppd[10826]: Serial link appears to be disconnected.
Nov  7 21:32:45 darkstar pppd[10826]: Connect time 2.5 minutes.
Nov  7 21:32:45 darkstar pppd[10826]: Sent 2482294812 bytes, received 0 bytes.
Nov  7 21:32:45 darkstar pppd[10826]: MPPE disabled
Nov  7 21:32:45 darkstar pptpd[10824]: GRE: read(fd=7,buffer=6095a0,len=8260) from network failed: status = -1 error = Protocol not available
Nov  7 21:32:45 darkstar pptpd[10824]: CTRL: GRE read or PTY write failed (gre,pty)=(7,6)
Nov  7 21:32:45 darkstar pptpd[10824]: CTRL: Reaping child PPP[10826]
Nov  7 21:32:45 darkstar pppd[10826]: Modem hangup
Nov  7 21:32:45 darkstar pppd[10826]: Connection terminated.
Nov  7 21:32:45 darkstar NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  7 21:32:45 darkstar pppd[10826]: Exit.
Nov  7 21:32:45 darkstar pptpd[10824]: CTRL: Client 192.168.1.1 control connection finished
```

---

