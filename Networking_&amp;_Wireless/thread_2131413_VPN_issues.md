---
title: "VPN issues"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by YaAqoB on 2013-04-01
Good morning all.
After quite a few years away from Ubuntu I have finally come back and am loving it. I'm currently running Ubuntu 12.10 x64.
This is my work computer and I'm required to VPN into many different clients to access their networks. For some reason I just can't get any VPN connection to establish. I have read the forums and google and tried all the different ideas but none solve my issue.
Also, I really don't want to be setting up the connections or connecting from the command line. I really want to use the Network Manager as it's designed to work.
Any help would be much appreciated.

Cheers in advance.

James

---

### Post by YaAqoB on 2013-04-01
I should add sorry that the VPN connections are OK at the other ends as my work mates can connect from their PCs and Macs and I can connect from my iPhone with no issues.

---

### Post by YaAqoB on 2013-04-01
[HTML]Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <info> Starting VPN service 'pptp'...
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 27481
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <info> VPN service 'pptp' appeared; activating connections
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <info> VPN plugin state changed: starting (3)
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <info> VPN connection 'Test VPN Connection' (Connect) reply received.
Apr  2 10:18:50 james-Ubuntu pppd[27485]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Apr  2 10:18:50 james-Ubuntu pppd[27485]: pppd 2.4.5 started by root, uid 0
Apr  2 10:18:50 james-Ubuntu pppd[27485]: Using interface ppp0
Apr  2 10:18:50 james-Ubuntu pppd[27485]: Connect: ppp0 <--> /dev/pts/2
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr  2 10:18:50 james-Ubuntu NetworkManager[981]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Apr  2 10:18:50 james-Ubuntu pptp[27488]: nm-pptp-service-27481 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr  2 10:18:50 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Apr  2 10:18:50 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr  2 10:18:50 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 38662).
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 59777
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is 00000000, recv_accm is FFFFFFFF
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Apr  2 10:18:51 james-Ubuntu pppd[27485]: EAP: peer reports authentication failure
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 59777
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Apr  2 10:18:51 james-Ubuntu pppd[27485]: Connection terminated.
Apr  2 10:18:51 james-Ubuntu avahi-daemon[971]: Withdrawing workstation service for ppp0.
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <warn> VPN plugin failed: 1
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_disp:pptp_ctrl.c:912]: Received Call Clear Request.
Apr  2 10:18:51 james-Ubuntu pptp[27488]: nm-pptp-service-27481 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr  2 10:18:51 james-Ubuntu pptp[27488]: nm-pptp-service-27481 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr  2 10:18:51 james-Ubuntu pptp[27496]: nm-pptp-service-27481 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr  2 10:18:51 james-Ubuntu pppd[27485]: Exit.
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <warn> VPN plugin failed: 1
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <info> VPN plugin state changed: stopped (6)
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <info> VPN plugin state change reason: 0
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr  2 10:18:51 james-Ubuntu NetworkManager[981]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Apr  2 10:18:56 james-Ubuntu NetworkManager[981]: <info> VPN service 'pptp' disappeared[/HTML]

---

### Post by RobertKH on 2013-04-02
Sorry to piggyback on this, but I am wanting to connect to my network via OpenVPN. I have a home server running Ubuntu 12.10 x64 as well. Are you using OpenVPN? Any chance to anyone knows of a decent tutorial on how to set this up?

---

