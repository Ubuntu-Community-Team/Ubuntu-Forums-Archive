---
title: "Possible bug in Gnome's NM PPTP plugin?"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Tempter on 2009-07-30
Hello All!

I'm using Ubuntu version 9.04 and I been trying to connect to a vpn service through Gnome's Network Manager PPTP plugin.

However, every time I try to connect the connection fails.

Now knowing that I configured everything correctly and am using the right user name and password I took a look at the messages in the syslog:

Jul 30 20:31:11  NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Jul 30 20:31:11  NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 5433 
Jul 30 20:31:11  NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Jul 30 20:31:11  NetworkManager: <info>  VPN plugin state changed: 3 
Jul 30 20:31:11  pppd[5436]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jul 30 20:31:11  NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Jul 30 20:31:11  pppd[5436]: pppd 2.4.5 started by root, uid 0
Jul 30 20:31:11  pppd[5436]: Using interface ppp0
Jul 30 20:31:11  pppd[5436]: Connect: ppp0 <--> /dev/pts/1
Jul 30 20:31:11  pptp[5438]: nm-pptp-service-5433 log[main: ptp.c:314]: The synchronous pptp option is NOT activated 
Jul 30 20:31:11  pptp[5448]: nm-pptp-service-5433 log[ctrlp_rep: ptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jul 30 20:31:11  pptp[5448]: nm-pptp-service-5433 log[ctrlp_disp: ptp_ctrl.c:739]: Received Start Control Connection Reply
Jul 30 20:31:11  pptp[5448]: nm-pptp-service-5433 log[ctrlp_disp: ptp_ctrl.c:773]: Client connection established.
Jul 30 20:31:12  pptp[5448]: nm-pptp-service-5433 log[ctrlp_rep: ptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jul 30 20:31:12  pptp[5448]: nm-pptp-service-5433 log[ctrlp_disp: ptp_ctrl.c:858]: Received Outgoing Call Reply.
Jul 30 20:31:12  pptp[5448]: nm-pptp-service-5433 log[ctrlp_disp: ptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 43776). 
Jul 30 20:31:42  pppd[5436]: LCP: timeout sending Config-Requests 
Jul 30 20:31:42  pppd[5436]: Connection terminated.
**Jul 30 20:31:42  NetworkManager: <info>  VPN plugin failed: 1 **
Jul 30 20:31:42  pppd[5436]: Modem hangup
Jul 30 20:31:42  pptp[5438]: nm-pptp-service-5433 warn[decaps_hdlc: ptp_gre.c:204]: short read (-1): Input/output error
Jul 30 20:31:42  pptp[5438]: nm-pptp-service-5433 warn[decaps_hdlc: ptp_gre.c:216]: pppd may have shutdown, see pppd log
Jul 30 20:31:42  pptp[5448]: nm-pptp-service-5433 log[callmgr_main: ptp_callmgr.c:234]: Closing connection (unhandled)
Jul 30 20:31:42  pptp[5448]: nm-pptp-service-5433 log[ctrlp_rep: ptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jul 30 20:31:42  pptp[5448]: nm-pptp-service-5433 log[call_callback: ptp_callmgr.c:79]: Closing connection (call state)
**Jul 30 20:31:42  NetworkManager: <info>  VPN plugin failed: 1** 
Jul 30 20:31:42  pppd[5436]: Exit.
**Jul 30 20:31:42  NetworkManager: <info>  VPN plugin failed: 1 **
Jul 30 20:31:42  NetworkManager: <info>  VPN plugin state changed: 6 
Jul 30 20:31:42  NetworkManager: <info>  VPN plugin state change reason: 0 
Jul 30 20:31:42  NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Jul 30 20:31:42  NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Jul 30 20:31:42  NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Jul 30 20:31:55  NetworkManager: <debug> [1249003915.002023] ensure_killed(): waiting for vpn service pid 5433 to exit 
Jul 30 20:31:55  NetworkManager: <debug> [1249003915.002277] ensure_killed(): vpn service pid 5433 cleaned up

As one can see the log states that the vpn has failed, is this do to a bug in the plugin?

And if not how can I troubleshoot this situation to resolve this problem?

Thanks in advance,

The Tempter

---

