---
title: "vpn dns ping fail 10.10"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by rexup on 2011-02-17
Hello all,
There is a VPN at work.  I have configured it using the Network Connections.  I have assigned the DNS that we use at work and the search domains to use this for.  
When  I try and ping the DNS instead of pinging xxx.xxx.1.99 it pings xxx.xxx.1.2

The only place I have found reference to the xxx.xxx.xxx.1.2 is in ip route but does not show up on the route -n

This I think is from my /etc/hosts file which adds the xxx.xxx.1.2 with a note # Added by NeworkManage.

I have tried to get other guys who use other flavours of Linux to help but I have not managed to get any closer.

One of the guys has connected successfully using Suse where he 
sudo route del default
sudo route add default ppp0
sudo ip route add IP_FOR_VPN_SERVER/PORT  via MY_HOME_ROUTER 

The last line returns
 RTNETLINK answers: File exists

Any help would be great.

---

