---
title: "problem trying to establish a vpn connection"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by seif12 on 2010-08-16
Hello 
i have been trying to connect to my vpn (created with windows xp )
in my local network but it fails it worked only one time 
i am using ubuntu lucid 10.04 
there is some part from the log it contain too many error
```
Aug 17 02:43:17 seif-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug 17 02:43:17 seif-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 21826
Aug 17 02:43:17 seif-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug 17 02:43:21 seif-laptop NetworkManager: <info>  VPN plugin state changed: 3
Aug 17 02:43:21 seif-laptop NetworkManager: <info>  VPN connection 'home' (Connect) reply received.
Aug 17 02:43:21 seif-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 17 02:43:21 seif-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 17 02:43:21 seif-laptop pptp[21866]: nm-pptp-service-21826 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Aug 17 02:43:24 seif-laptop pptp[21867]: nm-pptp-service-21826 warn[open_inetsock:pptp_callmgr.c:329]: connect: No route to host
Aug 17 02:43:24 seif-laptop pptp[21867]: nm-pptp-service-21826 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 192.168.1.3
Aug 17 02:43:24 seif-laptop pptp[21866]: nm-pptp-service-21826 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Aug 17 02:43:24 seif-laptop NetworkManager: <info>  VPN plugin failed: 1
```

so please help me

---

### Post by gombadi on 2010-08-16
> 
Aug 17 02:43:24 seif-laptop pptp[21867]: nm-pptp-service-21826 warn[open_inetsock:pptp_callmgr.c:329]: connect: No route to host
Aug 17 02:43:24 seif-laptop pptp[21867]: nm-pptp-service-21826 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 192.168.1.3


By the looks of things your machine can not sent packets to the remote server.

Check that you can ping from your machine to the remote vpn server - 192.168.1.3

---

### Post by seif12 on 2010-08-16
Sorry the machine  changed from ip when reconneting
i fixed her ip now and it's okay except the connection is a  bit slow 
thank you  for your  help :) .
any idea about the others things in the log (ifupdownd , synchronus pptp ) ?

---

