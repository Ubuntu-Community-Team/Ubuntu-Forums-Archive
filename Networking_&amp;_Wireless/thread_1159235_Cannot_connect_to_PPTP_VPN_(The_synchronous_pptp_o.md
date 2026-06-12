---
title: "Cannot connect to PPTP VPN (The synchronous pptp option is NOT activated )"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by m00 on 2009-05-14
Hello, I am trying to connect to a PPTP VPN at work, and I cannot accomplish that. I just switched from ArchLinux to Ubuntu, and it was working fine in the other distribution.

Any ideas?

```

May 14 13:39:04 m0-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
May 14 13:39:04 m0-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 8799 
May 14 13:39:04 m0-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
May 14 13:39:06 m0-desktop NetworkManager: <info>  VPN plugin state changed: 3 
May 14 13:39:06 m0-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
May 14 13:39:06 m0-desktop pppd[8804]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
May 14 13:39:06 m0-desktop pppd[8804]: pppd 2.4.5 started by root, uid 0
May 14 13:39:06 m0-desktop pptp[8807]: nm-pptp-service-8799 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
May 14 13:39:06 m0-desktop pppd[8804]: Using interface ppp0
May 14 13:39:06 m0-desktop pppd[8804]: Connect: ppp0 <--> /dev/pts/1
May 14 13:39:06 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
May 14 13:39:06 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 14 13:39:06 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 59325). 
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
May 14 13:39:07 m0-desktop pppd[8804]: LCP terminated by peer (^BM-^L9^N^@<M-Mt^@^@^BM-3)
May 14 13:39:07 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
May 14 13:39:10 m0-desktop pppd[8804]: Connection terminated.
May 14 13:39:10 m0-desktop NetworkManager: <info>  VPN plugin failed: 1 
May 14 13:39:10 m0-desktop pppd[8804]: Modem hangup
May 14 13:39:10 m0-desktop pptp[8807]: nm-pptp-service-8799 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
May 14 13:39:10 m0-desktop pptp[8807]: nm-pptp-service-8799 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
May 14 13:39:10 m0-desktop pptp[8816]: nm-pptp-service-8799 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
May 14 13:39:10 m0-desktop pptp[8816]: nm-pptp-service-8799 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
May 14 13:39:10 m0-desktop pptp[8816]: nm-pptp-service-8799 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
May 14 13:39:10 m0-desktop pppd[8804]: Exit.
May 14 13:39:10 m0-desktop NetworkManager: <info>  VPN plugin failed: 1 
May 14 13:39:10 m0-desktop NetworkManager: <info>  VPN plugin failed: 1 
May 14 13:39:10 m0-desktop NetworkManager: <info>  VPN plugin state changed: 6 
May 14 13:39:10 m0-desktop NetworkManager: <info>  VPN plugin state change reason: 0 
May 14 13:39:10 m0-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
May 14 13:39:10 m0-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May 14 13:39:22 m0-desktop NetworkManager: <debug> [1242322763.002598] ensure_killed(): waiting for vpn service pid 8799 to exit 
May 14 13:39:22 m0-desktop NetworkManager: <debug> [1242322763.002683] ensure_killed(): vpn service pid 8799 cleaned up 


```

---

### Post by m00 on 2009-05-20
Hello, any ideas why this is happening? I can't connect to "any" ptpp domain (hosted in windows, and linux)

---

### Post by nilgiri on 2009-05-30
[http://ubuntuforums.org/showthread.php?t=1095546&highlight=LCP+terminated+peer+VPN+PPTP]("http://ubuntuforums.org/showthread.php?t=1095546&highlight=LCP+terminated+peer+VPN+PPTP")

Be sure to read to the end to find all the tweaks.  It is annoying that there is no EAP option in the Network Manager GUI because then it would be fixable with trial and error.  Seems to be a fairly common problem.  Hopefully, it will show up soon in future releases.  If only I knew how to program for that app...

---

