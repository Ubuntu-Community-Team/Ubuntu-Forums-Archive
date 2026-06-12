---
title: "IPTables unable to nat trough VPN"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by cygnusx on 2012-04-27
Hello,

I have a VPN connection to a server on a remote location. I want other pc's to be able to reach the webserver on the remote location trough the VPN connector. But i can't get where i want. 

This is the situation:

```
VPN Server (and also the webserver): 10.0.0.2
          ^
          |
Router: 192.168.1.127 & 10.0.0.1 (openssh port is forwarded to 10.0.0.2)
          ^
          |
          |
VPN Connector: 192.168.1.148
          ^
          |
Client pc: 192.168.1.129
```
Also the ip of the vpn networks (called tun0) are:
VPN Server: 192.168.2.1
VPN Connector: 192.168.2.6

So, if i login to the VPN Connector, and do a wget 192.168.2.1:4848 it works fine.

That's good, the vpn connection works.

But what i want to do is: on the client pc go to the browser and go to 192.168.1.148:4848. (that's the vpn connector). Then the connector should forward it to the vpn showing me the webserver on 192.168.2.1 (the vpn server).

This is my IPTables setup:
```

iptables -t nat -A PREROUTING -p tcp -d 192.168.1.148 --dport 4848 -m state --state NEW,ESTABLISHED,RELATED -j DNAT -to 192.168.2.1:4848
iptables -t nat -A POSTROUTING -o tun0 MASQUERADE
```

So, i'm fairly new to iptables, What am i missing?

If i do a tcpdump on the vpn connector on tun0 i can see that the packets go trough?

```
13:31:02.850057 IP 192.168.1.129.52870 > 192.168.2.1.1337: Flags [S], seq 538959383, win 8192, options                          [mss 1460,nop,nop,sackOK], length 0
```

But if i do a tcpdump on the VPN server on tun0 nothing is happening.

I'm sorry that this is a long post, but what am i doing wrong? Please help!

---

### Post by Vishal Agarwal on 2012-04-27
Hi,

i read somewhere that MASQUERADE is useful for dynamic IP's; for fixed IP's it should be SNAT. That website were also accessable via temp Tunnal, and also the DNS entry was not visible from [www.network-tools.com](www.network-tools.com).
But after SNAT that problem was solved.

---

### Post by SeijiSensei on 2012-04-27
This could first of all be a routing problem.  Do the client PCs use the 192.168.1.148 address as the default gateway, or is the default pointing to a different router?  If the latter, then the simplest solution is to add a static route to the default gateway that forwards traffic for the 10.0.0.0/24 network via the 192.168.1.148 router.  

You can add the route to 10/24 on the individual client PCs, but it's simpler to add it to the default gateway. That method is also platform-independent.

If you take this approach, you shouldn't need to use iptables and masquerading at all.

---

