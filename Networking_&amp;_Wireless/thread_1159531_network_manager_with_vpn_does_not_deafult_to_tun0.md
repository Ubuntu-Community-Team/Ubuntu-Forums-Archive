---
title: "network manager with vpn does not deafult to tun0"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by mike310z on 2009-05-14
I can make a vpn connection to my work network without fail,  however I can't ping anything unless I specify the interface ```
ping -I tun0 <address>
```

If I manually set the default route I can ping, telent etc without a problem

```
route del default
route add default tun0
```

How do I get Network manager in 9.04 to do this automatically ?

I see these two messages in the log, is this broken ?

May 14 19:34:47 mike-desktop vpnc[4033]: can't open pidfile /var/run/vpnc/pid for writing
May 14 19:35:01 mike-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1

```
May 14 19:34:42 mike-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
May 14 19:34:42 mike-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 4022 
May 14 19:34:42 mike-desktop kernel: [ 1096.431722] tun: Universal TUN/TAP device driver, 1.6
May 14 19:34:42 mike-desktop kernel: [ 1096.431729] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 14 19:34:42 mike-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
May 14 19:34:42 mike-desktop NetworkManager: <info>  VPN plugin state changed: 1 
May 14 19:34:46 mike-desktop NetworkManager: <info>  VPN plugin state changed: 3 
May 14 19:34:46 mike-desktop NetworkManager: <info>  VPN connection 'company name' (Connect) reply received. 
May 14 19:34:47 mike-desktop kernel: [ 1101.087133] tun0: Disabled Privacy Extensions
May 14 19:34:47 mike-desktop NetworkManager: <info>  VPN connection 'company name' (IP Config Get) reply received. 
May 14 19:34:47 mike-desktop NetworkManager: <info>  VPN Gateway: gateway_ip 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Tunnel Device: tun0 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Internal IP4 Address: my_new_address 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Internal IP4 Prefix: 24 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Internal IP4 Point-to-Point Address: my_new_address 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Maximum Segment Size (MSS): 0 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Internal IP4 DNS: company_dns_1 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Internal IP4 DNS: company_dns_2 
May 14 19:34:47 mike-desktop NetworkManager: <info>  DNS Domain: company.com' 
May 14 19:34:47 mike-desktop NetworkManager: <info>  Login Banner: 
May 14 19:34:47 mike-desktop NetworkManager: <info>  ----------------------------------------- 
May 14 19:34:47 mike-desktop NetworkManager: <info>  (null) 
May 14 19:34:47 mike-desktop NetworkManager: <info>  ----------------------------------------- 
May 14 19:34:47 mike-desktop vpnc[4033]: can't open pidfile /var/run/vpnc/pid for writing
May 14 19:34:48 mike-desktop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf 
May 14 19:35:01 mike-desktop NetworkManager: <info>  VPN connection 'my company' (IP Config Get) complete. 
May 14 19:35:01 mike-desktop NetworkManager: <info>  (eth1): writing resolv.conf to /sbin/resolvconf 
May 14 19:35:01 mike-desktop NetworkManager: <info>  Policy set 'Auto linksys' (eth1) as default for routing and DNS. 
May 14 19:35:01 mike-desktop NetworkManager: <info>  VPN plugin state changed: 4 
May 14 19:35:01 mike-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1
```

Thanks Mike

---

### Post by TheRoot on 2009-05-19
Just open your NM and goto Configure VPN to edit your settings.
Then goto IPv4 Settings tab, and make the Method "Automatic VPN address only" and add the DNS Server of your remote VPN Network.

Then goto routes and select the "use this only for resources ...."

Now connect and you have access to VPN and Internet.


I hope this is what you are looking for !!!

---

