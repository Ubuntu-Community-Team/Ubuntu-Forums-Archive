---
title: "Jaunty can't connect to VPN"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by dvanzo on 2009-08-20
Ubuntu 9.04 32 bits
VPN (advanced): No EAP, MPPE enabled


Hi!

I'm trying to connect to a VPN (w2003) from my Ubuntu 9.04 without luck. I already search and test all the possible configurations... From the logs:

MESSAGES.LOG
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: pppd 2.4.5 started by root, uid 0
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Using interface ppp0
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Connect: ppp0 <--> /dev/pts/0
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Modem hangup
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Connection terminated.
Aug 20 13:46:49 ubuntu-vostro pppd[15934]: Exit.

DAEMON.LOG
Aug 20 13:46:36 ubuntu-vostro NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Aug 20 13:46:36 ubuntu-vostro NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 15905 
Aug 20 13:46:36 ubuntu-vostro NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN plugin state changed: 3 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN connection 'VpnCPCS' (Connect) reply received. 
Aug 20 13:46:37 ubuntu-vostro pptp[15910]: nm-pptp-service-15905 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Aug 20 13:46:37 ubuntu-vostro pptp[15915]: nm-pptp-service-15905 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Aug 20 13:46:37 ubuntu-vostro pptp[15915]: nm-pptp-service-15905 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 190.18.103.123
Aug 20 13:46:37 ubuntu-vostro pptp[15910]: nm-pptp-service-15905 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN plugin state changed: 6 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  VPN plugin state change reason: 0 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Aug 20 13:46:37 ubuntu-vostro NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 20 13:46:48 ubuntu-vostro NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Aug 20 13:46:48 ubuntu-vostro NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 15931 
Aug 20 13:46:48 ubuntu-vostro NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <debug> [1250786809.001086] ensure_killed(): waiting for vpn service pid 15905 to exit 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <debug> [1250786809.001511] ensure_killed(): vpn service pid 15905 cleaned up 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  VPN plugin state changed: 3 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  VPN connection 'VpnCPCS' (Connect) reply received. 
Aug 20 13:46:49 ubuntu-vostro pptp[15936]: nm-pptp-service-15931 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Aug 20 13:46:49 ubuntu-vostro pptp[15941]: nm-pptp-service-15931 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Aug 20 13:46:49 ubuntu-vostro pptp[15941]: nm-pptp-service-15931 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 190.18.103.123
Aug 20 13:46:49 ubuntu-vostro pptp[15936]: nm-pptp-service-15931 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 13:46:49 ubuntu-vostro last message repeated 2 times
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  VPN plugin state changed: 6 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  VPN plugin state change reason: 0 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Aug 20 13:46:49 ubuntu-vostro NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 20 13:47:01 ubuntu-vostro NetworkManager: <debug> [1250786821.002496] ensure_killed(): waiting for vpn service pid 15931 

Any idea??

Regards,

Daniel

---

