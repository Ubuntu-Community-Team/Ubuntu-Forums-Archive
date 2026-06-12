---
title: "Please help me! Iptables 1-1 nat"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by Gary Maurizi on 2013-05-17
I have been trying to accomplish a pretty darn simple task with iptables for a week now, seriously. I simply want one to one nat, that's all. I want any requests from my Ubuntu router box and the clients behind it to the address 172.20.2.99 to get sent to 10.1.150.20. I have tried many variations of 1-1 nat in iptables and NOTHING has worked. I have enabled IP Forwarding, and tried the following: 
**01). **net.ipv4.conf.default.forwarding=1 [B]
02). [/B]ifconfig eth1:1 172.20.2.99 netmask 255.255.255.0 broadcast 172.20.2.255 [B]
03).[/B] iptables -t nat -I PREROUTING -d 172.20.2.99 -j DNAT --to-destination 10.1.150.20 [B]
04).[/B] iptables -t nat -I POSTROUTING -s 10.1.150.20 -j SNAT --to-source 172.20.2.99 [B]
05). [/B]route add -net 10.1.150.0 netmask 255.255.255.0 gw 172.20.2.1(the route for 10.1.150.20 address). 
I can ping 10.1.150.20, I can ping 172.20.2.99, if I try to ssh 172.20.2.99 I end up ssh'ing into the box I am sitting in front of and NOT the box with the 10.1.150.20 IP Address, so NAT is NOT working. Please help guys, what am I missing here?

---

### Post by Doug S on 2013-05-17
I think we need to know a little bit more first (at least, I do).
Do you have two NICs (network interface cards) in the box or 1? If two, what is the IP address of the second one? If one, then you are trying to send them back out through the same interface with addreses re-mapped, correct?

---

### Post by The Cog on 2013-05-17
It should not be a problem. Items 1, 2 and 4 look OK to me, and I don't think you need item 3 unless the 10.1.150.20 server makes connections back to the clients. I think there is something missing. A fuller explanation might help. Like a list of all the addresses on the Ubuntu router, the address of the clients. Where are you pinging from, what is "the box I am sitting in front of"?

Also, using tcpdump to capture the packets as you make a test connection would be useful:
```
sudo tcpdump -enp -i any
```
This list of addresses would also be useful:
```
ip addr list
```
Also the output of this command, just before and just after making that test connection:
```
sudo iptables-save -c
```

---

### Post by Gary Maurizi on 2013-05-17
This box will be a router/firewall. There are two NICS in this box.
eth0 --> (PublicWANIP)
eth1 --> (PrivateLANIP with DHCP/bind9 on eth1)
Currently no machines are plugged into eth1, I am simply trying to get NAT working before I can hook up the LAN clients. I assume if NAT is not working on the box the nat rules live on, they are certainly not going to work for clients behind it on the LAN side.

---

### Post by Gary Maurizi on 2013-05-17
Good advice is good advice. Thank You

---

### Post by Gary Maurizi on 2013-05-17
delete

---

### Post by Gary Maurizi on 2013-05-17
I apologize I am having some issues with the quick-reply box not letting me insert lines/white space. Also I just realized there are some un-needed iptables rules lingering from my previous testing, but I assure you I have tried with my default policies set to accept, with no other rules in place except for the pre and post-route nat rules. Thanks. :)

---

### Post by The Cog on 2013-05-17
You may want to edit that long post - it contains your server's public IP address. You may not want that to remain on this public forum.

Please use the Go Advanced button and then the "#" button above the editor to change relevant quotes into monospaced font in future - it really helps readability.

Local output doesn't pass though the PREROUTING chain so if you want to do it locally as well as to routed traffic, you also need to add this rule:
```
iptables -t nat -I OUTPUT -d 172.20.2.99 -j DNAT --to-destination 10.1.150.20
```

---

### Post by Gary Maurizi on 2013-05-17
oh my, I knew it was going to be something simple. Thank You! I do not mind much if this one public address is known, it will not be used after today. :) but thank you for your concern.

---

### Post by The Cog on 2013-05-17
I don't think your plan will work. Your clients and your gateway to the server you are NATting are both on the same network.

The client's outgoing request will pass through your router because you have configured the destination address as a secondary, which will make your router respond to ARP requests and thereby attract packets from the clients. But then the destination server replies to the clients, the gateway 172.20.2.1 will send the reply packet direct to the client (it will ARP to get the client's MAC address). Without the reply passing back through the Ubuntu router, the reply will not be un-natted and the client won't recognise it - will probably send a reset.

You have to find some way of making sure that both directions of the conversation go through your Ubuntu NAT router.

---

