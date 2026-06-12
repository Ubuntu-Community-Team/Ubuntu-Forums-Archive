---
title: "Unable to connect to MS VPN after upgrading to ubuntu intrepid"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by thasan on 2008-12-27
Upgraded to intrepid and my vpn connection to work is not working. It was working fine on the earlier release.

Looks like the LCP connection is getting closed by the peer.

Code:
```
Dec 27 10:27:49 thasan-server NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Dec 27 10:27:49 thasan-server NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 12066
Dec 27 10:27:49 thasan-server NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Dec 27 10:27:49 thasan-server NetworkManager: <info>  VPN plugin state changed: 3
Dec 27 10:27:49 thasan-server NetworkManager: <info>  VPN connection 'Company Name' (Connect) reply received.
Dec 27 10:27:49 thasan-server pppd[12070]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 27 10:27:49 thasan-server pppd[12070]: pppd 2.4.4 started by root, uid 0
Dec 27 10:27:49 thasan-server pppd[12070]: Using interface ppp0
Dec 27 10:27:49 thasan-server pppd[12070]: Connect: ppp0 <--> /dev/pts/1
Dec 27 10:27:49 thasan-server pptp[12071]: nm-pptp-service-12066 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 27 10:27:49 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 27 10:27:49 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 27 10:27:49 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 27 10:27:50 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 27 10:27:50 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 27 10:27:50 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 41107).
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Dec 27 10:27:51 thasan-server pppd[12070]: LCP terminated by peer (^?^[<M-l^@<M-Mt^@^@^BM-3)
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Dec 27 10:27:51 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Dec 27 10:27:54 thasan-server NetworkManager: <info>  VPN plugin failed: 1
Dec 27 10:27:54 thasan-server pppd[12070]: Connection terminated.
Dec 27 10:27:54 thasan-server pptp[12071]: nm-pptp-service-12066 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 27 10:27:54 thasan-server pptp[12071]: nm-pptp-service-12066 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 27 10:27:54 thasan-server pptp[12076]: nm-pptp-service-12066 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 27 10:27:54 thasan-server pptp[12076]: nm-pptp-service-12066 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request
```



I am running 64-bit intrepid.  Not sure if I have to install some vpn plugin or anything.
I would appreciate if anyone can help me resolve this.  Please let me know if you need any more info.  
The above message is from syslog.

---

### Post by thasan on 2009-01-04
I solved this problem after following the directions of user user9 at
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48681](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/48681)

Just in case if anyone is still having the same issue as I did,

I had to do the following:

1. Add DOMAIN/USERNAME to username field and leave NT Domain empty.
2. Disable CHAP and PAP in the Advanced settings.
3. Enable MPPE under Security and Compression (left the drop-down to default, changing it to 128 disabled this option)
4. Edited system/networking/connections/2/vpn/ to include refuse-eap with value yes.
This path after "connections" maybe different for you depending on the number of vpn connections you have setup.

The above steps solved my problem.

---

### Post by thasan on 2009-01-04
BTW, step 4 is in gconf-editor...:o

---

