---
title: "VPN finally, but no internet"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by markgobbin on 2009-03-10
Basically, it's taken me weeks to get VPN going (because i can test the settings only when i'm at university). So I've done the refuse-eap fix and it finally connects, but... no internet. And the proxy host is unrecognised. So, firstly this is the syslog that i get from connecting to vpn:

```
Mar 10 17:05:24 mark-netbook pppd[6181]: CHAP authentication succeeded
Mar 10 17:05:24 mark-netbook pppd[6181]: MPPE 128-bit stateless compression enabled
Mar 10 17:05:26 mark-netbook pppd[6181]: Cannot determine ethernet address for proxy ARP
Mar 10 17:05:26 mark-netbook pppd[6181]: local  IP address 137.92.194.36
Mar 10 17:05:26 mark-netbook pppd[6181]: remote IP address 137.92.194.1
Mar 10 17:05:26 mark-netbook pppd[6181]: primary   DNS address 137.92.98.50
Mar 10 17:05:26 mark-netbook pppd[6181]: secondary DNS address 137.92.98.47
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  VPN connection 'UCanberra' (IP Config Get) reply received. 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  VPN Gateway: 137.92.194.1 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Tunnel Device: ppp0 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Internal IP4 Address: 137.92.194.36 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Internal IP4 Prefix: 32 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Internal IP4 DNS: 137.92.98.50 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Internal IP4 DNS: 137.92.98.47 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  DNS Domain: '(none)' 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  Login Banner: 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  ----------------------------------------- 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  (null) 
Mar 10 17:05:26 mark-netbook NetworkManager: <info>  ----------------------------------------- 
Mar 10 17:05:27 mark-netbook NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf 
Mar 10 17:05:27 mark-netbook NetworkManager: <info>  VPN connection 'UCanberra' (IP Config Get) complete. 
Mar 10 17:05:27 mark-netbook NetworkManager: <info>  VPN plugin state changed: 4 
Mar 10 17:05:27 mark-netbook nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

Ok so then I enter the proxy host into firefox which is proxyhost.canberra.edu.au port 80 which is the proper setting according to instructions and other uni computers. And it fails. so i looked up the ip address of proxyhost from a university computer and just tried to ping the address from ubuntu

```

$ ping 137.92.98.114
connect: Network is unreachable

```

i also try 137.92.98.50, some dns (and also fails), and the syslog at the exact time that i ping follows:

```
Mar 10 17:09:04 mark-netbook NetworkManager: <debug> [1236665344.347954] periodic_update(): Roamed from BSSID 00:18:4D:C6:E8:63 (UCWIFI) to (none) ((none)) 
Mar 10 17:09:10 mark-netbook NetworkManager: <debug> [1236665350.352092] periodic_update(): Roamed from BSSID (none) ((none)) to 00:18:4D:C6:E8:63 (UCWIFI) 
Mar 10 17:09:21 mark-netbook pptp[6190]: nm-pptp-service-6178 log[logecho:pptp_ctrl.c:677]: Echo Reply received.
```

i don't know how to interpret that. other than it's roaming, but whether the echo reply has anything to do with my ping I can't say, (i'm hazy on network theory, plus i'm a linux n00b ;) )

And yes i have suddenly noticed that the point to point address was 0.0.0.0. Still i don't know what it means or what to do :confused: 
Ideas? I can't find any more solutions at this point and i really need this to work

---

