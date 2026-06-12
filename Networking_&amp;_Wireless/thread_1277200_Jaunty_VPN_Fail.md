---
title: "Jaunty VPN Fail"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by dcsonntag on 2009-09-28
My VPN host vendor looked this over, and was clueless. I can connect to their service from all of my various OS except for Ubuntu Jaunty.

Here is the error code, appreciate any suggestions.

Thanks.

```
&#65279;NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 4817 
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
NetworkManager: <info>  VPN plugin state changed: 1 
NetworkManager: <info>  VPN plugin state changed: 3 
pppd[4820]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
NetworkManager: <info>  VPN connection 'Banana' (Connect) reply received. 
pppd[4820]: pppd 2.4.5 started by root, uid 0
pptp[4822]: nm-pptp-service-4817 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
pppd[4820]: Using interface ppp0
pppd[4820]: Connect: ppp0 <--> /dev/pts/0
pptp[4832]: nm-pptp-service-4817 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
pptp[4832]: nm-pptp-service-4817 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 256). 
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
pptp[4832]: nm-pptp-service-4817 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
pppd[4820]: CHAP authentication failed
pppd[4820]: CHAP authentication failed
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
pptp[4832]: nm-pptp-service-4817 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
pppd[4820]: Connection terminated.
NetworkManager: <info>  VPN plugin failed: 1 
pptp[4832]: nm-pptp-service-4817 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
pptp[4822]: nm-pptp-service-4817 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
pptp[4822]: nm-pptp-service-4817 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
pptp[4832]: nm-pptp-service-4817 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
pptp[4832]: nm-pptp-service-4817 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
pptp[4832]: nm-pptp-service-4817 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
NetworkManager: <info>  VPN plugin failed: 1 
pppd[4820]: Exit.
NetworkManager: <info>  VPN plugin state changed: 6 
NetworkManager: <info>  VPN plugin state change reason: 0 
NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
NetworkManager: <info>  (ra0): writing resolv.conf to /sbin/resolvconf 
NetworkManager: <info>  Policy set 'Auto Sushiban' (ra0) as default for routing and DNS. 
kernel: [ 1175.808784] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 513
NetworkManager: <debug> [1254118065.002143] ensure_killed(): waiting for vpn service pid 4817 to exit 
NetworkManager: <debug> [1254118065.002264] ensure_killed(): vpn service pid 4817 cleaned up 
```

---

