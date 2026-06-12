---
title: "VPN Connection to ISP Fails"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by matrixblue on 2009-04-11
I have package with my ISP where I have to sign into a VPN connection to get internet access. I installed the network manager pptp package.

My ISP told  that in Windows I am supposed to disable the security settings and I did this in Ubuntu but it fails no matter what combination I use.

---

### Post by matrixblue on 2009-04-11
This is the output I get: 

Apr 11 20:05:47 barry-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7923 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 1 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 3 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Apr 11 20:05:47 barry-desktop pppd[7924]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Apr 11 20:05:47 barry-desktop pppd[7924]: pppd 2.4.4 started by root, uid 0
Apr 11 20:05:47 barry-desktop pptp[7926]: nm-pptp-service-7923 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Apr 11 20:05:47 barry-desktop pppd[7924]: Using interface ppp0
Apr 11 20:05:47 barry-desktop pppd[7924]: Connect: ppp0 <--> /dev/pts/1
Apr 11 20:05:47 barry-desktop pptp[7927]: nm-pptp-service-7923 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Apr 11 20:05:47 barry-desktop pptp[7927]: nm-pptp-service-7923 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 10.6.0.6
Apr 11 20:05:47 barry-desktop pptp[7926]: nm-pptp-service-7923 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Apr 11 20:05:47 barry-desktop pppd[7924]: Modem hangup
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin failed: 1 
Apr 11 20:05:47 barry-desktop pppd[7924]: Connection terminated.
Apr 11 20:05:47 barry-desktop pppd[7924]: Exit.
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin failed: 1 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 6 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state change reason: 0 
Apr 11 20:05:47 barry-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  Policy set 'Home' (eth0) as default for routing and DNS. 
Apr 11 20:05:59 barry-desktop NetworkManager: <debug> [1239494759.668320] ensure_killed(): waiting for vpn service pid 7923 to exit 
Apr 11 20:05:59 barry-desktop NetworkManager: <debug> [1239494759.668583] ensure_killed(): vpn service pid 7923 cleaned up

---

### Post by matrixblue on 2009-04-11
This is the output I get: 

Apr 11 20:05:47 barry-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7923 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 1 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 3 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Apr 11 20:05:47 barry-desktop pppd[7924]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Apr 11 20:05:47 barry-desktop pppd[7924]: pppd 2.4.4 started by root, uid 0
Apr 11 20:05:47 barry-desktop pptp[7926]: nm-pptp-service-7923 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Apr 11 20:05:47 barry-desktop pppd[7924]: Using interface ppp0
Apr 11 20:05:47 barry-desktop pppd[7924]: Connect: ppp0 <--> /dev/pts/1
Apr 11 20:05:47 barry-desktop pptp[7927]: nm-pptp-service-7923 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Apr 11 20:05:47 barry-desktop pptp[7927]: nm-pptp-service-7923 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 10.6.0.6
Apr 11 20:05:47 barry-desktop pptp[7926]: nm-pptp-service-7923 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Apr 11 20:05:47 barry-desktop pppd[7924]: Modem hangup
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin failed: 1 
Apr 11 20:05:47 barry-desktop pppd[7924]: Connection terminated.
Apr 11 20:05:47 barry-desktop pppd[7924]: Exit.
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin failed: 1 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state changed: 6 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  VPN plugin state change reason: 0 
Apr 11 20:05:47 barry-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr 11 20:05:47 barry-desktop NetworkManager: <info>  Policy set 'Home' (eth0) as default for routing and DNS. 
Apr 11 20:05:59 barry-desktop NetworkManager: <debug> [1239494759.668320] ensure_killed(): waiting for vpn service pid 7923 to exit 
Apr 11 20:05:59 barry-desktop NetworkManager: <debug> [1239494759.668583] ensure_killed(): vpn service pid 7923 cleaned up

---

