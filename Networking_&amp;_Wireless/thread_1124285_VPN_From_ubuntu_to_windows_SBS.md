---
title: "VPN From ubuntu to windows SBS"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Millay on 2009-04-13
hi All i have been working on this issue for some time, i am runningubuntu 8.10 and have not been able to get it to connect to a SBS VPN at all. 

I have followed all the different peices of advice i have found through google to no avail. I would really appreciate some help, heres the log output from my last attempt

```

Apr 13 13:11:05 andym-laptop pppd[6535]: Modem hangup
Apr 13 13:11:05 andym-laptop pppd[6535]: Exit.
Apr 13 13:11:05 andym-laptop NetworkManager: <info>  VPN plugin failed: 1 
Apr 13 13:11:05 andym-laptop NetworkManager: <info>  VPN plugin state changed: 6 
Apr 13 13:11:05 andym-laptop NetworkManager: <info>  VPN plugin state change reason: 0 
Apr 13 13:11:05 andym-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr 13 13:11:05 andym-laptop NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Apr 13 13:11:05 andym-laptop NetworkManager: <info>  Policy set 'Auto BTHomeHub-D951' (wlan0) as default for routing and DNS. 
Apr 13 13:11:17 andym-laptop NetworkManager: <debug> [1239624677.467492] ensure_killed(): waiting for vpn service pid 6530 to exit 
Apr 13 13:11:17 andym-laptop NetworkManager: <debug> [1239624677.467943] ensure_killed(): vpn service pid 6530 cleaned up 

```

---

