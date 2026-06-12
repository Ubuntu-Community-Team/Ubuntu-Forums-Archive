---
title: "Ping through subinterfaces"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by mannyto210 on 2011-06-22
Cheers 'ubuntuers'!

I've tried searching for some help with almost no results. I have a machine installed with ubuntu desktop 10.04. It has one NIC (eth0) but I've configured many subinterfaces (with vlan tagging) as this is a network monitoring box. Everything works pretty well. I have problems when I try to ping Internet sites (say googl, for example) through different interfaces. I have setup a default route to reach sites out of my LAN. If I just issue ping <site> it works fine. I've tried to do ping -I <site> but I get no response back. I've done tcpdump (filtering to see traffic to/from the site I'm pinging) and I only see the ping requests being sent out. Any ideas?

Many thanks!

---

### Post by mannyto210 on 2011-07-01
...anyone...? :(

---

### Post by batman01 on 2011-07-02
You may be confused by the -I command. It doesn't define what interface your ping goes out of, if simply defines what will we set as the IP source address of the packet. The packet will still get sent out of the interface defined by the route table.

The network that is shared by your Linux box and your internet router is routable from the internet so when you do a normal ping the packet is routed out of that interface and the source address is picked up as it exits the interface. Hence the response is to a routable network.

When you use -I you send the packet out of the same interface to the router but the packet now has a source address of the interface that you specified. If the internet or internet router has no knowledge of the other networks on your sub-interfaces then the response will never arrive.

Simple really.

---

### Post by mannyto210 on 2011-07-03
Thankyou so much for your reply batman01! 
I want to check reachability and delay from different networks. I limit bandwidth toward the Internet on some of these and I'd like to monitor that precisely (hence the need for the subinterfaces). Do you (or anyone reading this post) know of a way to do this? Thanks!

---

### Post by mannyto210 on 2011-07-11
Anyone has any suggestions?

---

### Post by jimmah6786 on 2012-12-09
@mannyto210

Are you trying to do "routing-on-a-stick"? Or inter-VLAN routing? If so you need to make a subinterface that has a layer 3 IP address for each network and at the same make sure that it is a turnk port (meaning all VLANs at layer2 can access the port). 

Make sure ubuntu is set to **ip forward**, check 
```
cat /proc/sys/net/ipv4/ip_forward 
```
Make sure it's a 1, if not change it.

Last check IP tables, as you need to masquerade or NAT outbound connections to the Internet. Assuming you are using private address(192.168.0.0/24, 172.16.0.0/16, 10.0.0.0/8)spaces, they are non-routable on the internet. Your service provider will see it and drop the packet.

I use Ubuntu server 12.04 as router/firewall only using two interface cards for 4 networks (1 being gateway of last resort).

Hope that helps!

---

