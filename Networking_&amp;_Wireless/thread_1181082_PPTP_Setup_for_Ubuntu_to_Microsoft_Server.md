---
title: "PPTP Setup for Ubuntu to Microsoft Server"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by RKCMUser on 2009-06-07
Hello:

I've been working with a Ubuntu 8.04.2 to Microsoft PPTP setup for over a week now.  I've made some progress, but it's still not totally working.  Here is what's going on.

I'm running a fresh install of Ubuntu 8.04.2 at home (Running a Linksys router with IP scheme of 192.168.51.x), and trying to connect to my work Windows Server 2003 via PPTP (also running a Linksys with IP scheme of 192.168.50.x). My WinXP computer connects to the WORK PPP without issue and have used it for a while now without any problems.

On Ubuntu, I installed the Network Manager & VPN Connection manager.  From there, I am able to configure a VPN connection.  Here is my setup (also shown in my screenshots):

* Connection
- Provided name of connection
- Provided name of gateway

*Authentication
- Selected "Refuse EAP", "Refuse CHAP", "Refuse MS CHAP".  (This is because MS CHAP V2 should be used to establish the connection)

* Compression & Encryption
- Selected "Require MPPE encryption", "Require 128 encryption", "Enable stateful MPPE"
- All other boxes are unchecked

* PPP Options
- Selected "Use Peer DNS" and "Exclusive device access"

*Routing
- Selected "Only use VPN Connection..." and defined my route: 192.168.50.0/24  (This is because I want to access the entire range of IPs on my WORK network)

Here is what happens:

I am able to authenticate and connect to the network and receive an IP.  I then open a couple of terminal windows and start pinging a couple of servers.  The pings run continuously for 30 minutes with a single hiccup.  When I try to access the remote network intranet (or even an remote desktop session), a part of the page will appear then just sits.  Looking at the terminal windows, the ping just stops. Opening yet another terminal window to restart a ping gives me "ping: sendmsg: Network is unreachable".  I've included the log below of the entire test.

I've tried all kinds of settings and adjustments, and get figure this one out.  Anyone have any thoughts?

Thanks!

RKCMUser
=================================================================

Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  Will activate VPN connection 'rkcm2', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'administrator', vpn_data 'ppp-connection-type / pptp / pptp-remote / rkcm.dyndns.org / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / no / routes / 192.168.50.0/24 / use-routes / yes', route '192.168.50.0/24'. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 1 of 4 (Connection Prepare) scheduled... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6715) 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 1 of 4 (Connection Prepare) complete. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 3 of 4 (Connect) scheduled... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 3 of 4 (Connect) sending connect request. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jun  7 09:58:54 rkcmlinux pppd[6716]: Plugin nm-pppd-plugin.so loaded.
Jun  7 09:58:54 rkcmlinux pppd[6716]: nm-pppd-plugin: plugin initialized.
Jun  7 09:58:54 rkcmlinux pppd[6717]: pppd 2.4.4 started by root, uid 0
Jun  7 09:58:54 rkcmlinux pppd[6717]: Using interface ppp0
Jun  7 09:58:54 rkcmlinux pppd[6717]: Connect: ppp0 <--> /dev/pts/1
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 3 of 4 (Connect) reply received. 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jun  7 09:58:54 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jun  7 09:58:54 rkcmlinux pptp[6720]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jun  7 09:58:54 rkcmlinux pptp[6723]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun  7 09:58:54 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jun  7 09:58:54 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jun  7 09:58:55 rkcmlinux pppd[6717]: nm-pppd-plugin: CHAP check hook.
Jun  7 09:58:55 rkcmlinux pptp[6723]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jun  7 09:58:57 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jun  7 09:58:57 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 31811). 
Jun  7 09:58:59 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Jun  7 09:58:59 rkcmlinux pptp[6723]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jun  7 09:58:59 rkcmlinux pptp[6723]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Jun  7 09:58:59 rkcmlinux pppd[6717]: nm-pppd-plugin: CHAP credentials requested.
Jun  7 09:58:59 rkcmlinux pppd[6717]: CHAP authentication succeeded
Jun  7 09:59:02 rkcmlinux pppd[6717]: MPPE 128-bit stateless compression enabled
Jun  7 09:59:03 rkcmlinux pppd[6717]: Cannot determine ethernet address for proxy ARP
Jun  7 09:59:03 rkcmlinux pppd[6717]: local  IP address 192.168.50.113
Jun  7 09:59:03 rkcmlinux pppd[6717]: remote IP address 192.168.50.118
Jun  7 09:59:03 rkcmlinux pppd[6717]: primary   DNS address 192.168.50.200
Jun  7 09:59:03 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 4 of 4 (IP Config Get) reply received. 
Jun  7 09:59:04 rkcmlinux NetworkManager: <info>  Clearing nscd hosts cache. 
Jun  7 09:59:04 rkcmlinux NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun  7 09:59:04 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) Stage 4 of 4 (IP Config Get) complete. 
Jun  7 09:59:04 rkcmlinux NetworkManager: <info>  VPN Activation (rkcm2) successful. 
Jun  7 09:59:04 rkcmlinux NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 4. 
Jun  7 09:59:54 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Request received.
Jun  7 09:59:54 rkcmlinux pptp[6723]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Jun  7 10:00:54 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Request received.
Jun  7 10:00:54 rkcmlinux pptp[6723]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Jun  7 10:00:54 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:01:54 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:02:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:03:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:04:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:05:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:06:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:07:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Jun  7 10:07:55 rkcmlinux pptp[6723]: anon log[logecho:pptp_ctrl.c:678]: no more Echo Reply/Request packets will be reported.
Jun  7 10:17:01 rkcmlinux /USR/SBIN/CRON[6774]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  7 10:25:45 rkcmlinux pptp[6720]: anon warn[decaps_gre:pptp_gre.c:324]: short read (-1): Message too long
Jun  7 10:25:45 rkcmlinux pptp[6723]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Jun  7 10:25:45 rkcmlinux pptp[6723]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jun  7 10:25:45 rkcmlinux pptp[6723]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jun  7 10:25:45 rkcmlinux pppd[6717]: Modem hangup
Jun  7 10:25:45 rkcmlinux pppd[6717]: Connect time 26.7 minutes.
Jun  7 10:25:45 rkcmlinux pppd[6717]: Sent 271997 bytes, received 289832 bytes.
Jun  7 10:25:45 rkcmlinux pppd[6717]: MPPE disabled
Jun  7 10:25:45 rkcmlinux pppd[6717]: Connection terminated.
Jun  7 10:25:45 rkcmlinux pppd[6717]: Exit.

---

### Post by RKCMUser on 2009-06-08
Bump

---

