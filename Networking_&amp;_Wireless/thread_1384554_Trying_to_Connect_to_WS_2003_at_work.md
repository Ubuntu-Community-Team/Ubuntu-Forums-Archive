---
title: "Trying to Connect to WS 2003 at work"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by iv76erson03 on 2010-01-18
I am trying to connect to my server at work through a VPN connection. I installed the PPTP VPN Connection Manager and configured the connection using the server's IP address and my user and password. When I click on the VPN connection in network manager, nothing happens. Do I need to install something else or is there an easier way to do this?

With my Windows 7 machine, it automatically connects using just the IP address and username and password. I was hoping to find an easy way to do the same in ubuntu. Thanks.

---

### Post by Fire_Chief on 2010-01-18
If you check the logs, do you see status messages on the connection attempt?
```
tail -n 100 /var/log/daemon.log
```

---

### Post by iv76erson03 on 2010-01-18
Here you go, maybe you can figure out what I'm doing wrong. Thanks for the reply.

Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3786
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  VPN plugin state changed: 1
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  VPN plugin state changed: 3
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  VPN connection 'HDI' (Connect) reply received.
Jan 18 14:58:34 caleb-desktop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'HDI' failed to connect: 'No VPN secrets!'.
Jan 18 14:58:34 caleb-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan 18 14:58:34 caleb-desktop NetworkManager: <info>  Policy set '*********' (wlan0) as default for routing and DNS.
Jan 18 14:58:47 caleb-desktop NetworkManager: <debug> [1263848327.002642] ensure_killed(): waiting for vpn service pid 3786 to exit
Jan 18 14:58:47 caleb-desktop NetworkManager: <debug> [1263848327.002730] ensure_killed(): vpn service pid 3786 cleaned up

---

### Post by Fire_Chief on 2010-01-18
The problem is indicated by this line
```
Jan 18 14:58:34 caleb-desktop NetworkManager: <WARN> nm_vpn_connection_connect_cb(): VPN connection 'HDI' failed to connect: 'No VPN secrets!'.
```

I found another thread here that looks like someone figured out the steps to make this work. Give it a shot.

[http://ubuntuforums.org/showpost.php?p=8261958&postcount=6]("http://ubuntuforums.org/showpost.php?p=8261958&postcount=6")

Cheers!

---

