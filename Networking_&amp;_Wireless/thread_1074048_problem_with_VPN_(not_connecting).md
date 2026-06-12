---
title: "problem with VPN (not connecting)"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by rancsj on 2009-02-18
I am trying to use the VPN and cannot get it to work. I am using Ubuntu 8.1Intrepid 64bit.  I create a VPN connection (actually I imported it from a pcf file). When I try to connect I get the message: The VPN connection to 'XXXX' failed. The syslog has the following:

Feb 18 19:25:44 frodo NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 10111 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN plugin state changed: 3 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN connection 'XXXX' (Connect) reply received. 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN plugin failed: 1 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN plugin state changed: 6 
Feb 18 19:25:44 frodo NetworkManager: <info>  VPN plugin state change reason: 0 
Feb 18 19:25:44 frodo NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Feb 18 19:25:44 frodo NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Feb 18 19:25:44 frodo NetworkManager: <info>  Policy set 'Auto Courtyard' (wlan0) as default for routing and DNS. 

This connection works from a Windows box (even from with a Windows VM on the same box).

Please help.
Thanks,
Randy

---

