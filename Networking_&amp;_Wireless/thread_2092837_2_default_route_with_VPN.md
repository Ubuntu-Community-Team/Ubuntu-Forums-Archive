---
title: "2 default route with VPN"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by Catalyph on 2012-12-09
I have a VPN that I would like all traffic to go through except for a few specific ports such as ssh and webmin.

i have tried to get it working a few times without success.
here is what i have:

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c8:94:df
          inet addr:192.168.X.10  Bcast:192.168.X.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fec8:94df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7309513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8866769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4441696327 (4.4 GB)  TX bytes:9823820555 (9.8 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2839546 (2.8 MB)  TX bytes:2839546 (2.8 MB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:172.16.XX.XX  P-t-P:172.16.XX.X  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:54772 (54.7 KB)  TX bytes:37466 (37.4 KB)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
172.16.36.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
195.60.76.223   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0

---

### Post by Catalyph on 2012-12-09
No-one has any input?

I was thinking maybe i can do this through iptables, but i don't know enough about iptables to write something for it.

---

### Post by SeijiSensei on 2012-12-09
You don't tell us the address of the remote PPTPD server, so I'll use 10.1.1.1 as its address. Presumably it has a public Internet address.

The trick is to tell your computer to use the Internet to reach 10.1.1.1, but to send everything else over the tunnel.  Something like this:

```

ip route add 10.1.1.1/32 via 192.168.0.1
ip route del default
ip route add default 172.16.36.1

```

Now your computer will send the encrypted traffic to the external PPTP server, but use the tunnel for everything else.

Adapting this to exclude certain protocols like SSH is tricky.  You would probably need some iptables rules for that, since routing doesn't pay attention to ports.

By the way, there's no need to obfuscate private addresses like 192.168.x.y.  No one can reach them from the Internet anyway as they are not publicly routed.

---

### Post by Catalyph on 2012-12-10
> **SeijiSensei said:**
> You don't tell us the address of the remote PPTPD server, so I'll use 10.1.1.1 as its address. Presumably it has a public Internet address.

The trick is to tell your computer to use the Internet to reach 10.1.1.1, but to send everything else over the tunnel.  Something like this:

```

ip route add 10.1.1.1/32 via 192.168.0.1
ip route del default
ip route add default 172.16.36.1

```Now your computer will send the encrypted traffic to the external PPTP server, but use the tunnel for everything else.

Adapting this to exclude certain protocols like SSH is tricky.  You would probably need some iptables rules for that, since routing doesn't pay attention to ports.

By the way, there's no need to obfuscate private addresses like 192.168.x.y.  No one can reach them from the Internet anyway as they are not publicly routed.

I basically already have this working where everything leaving out to the internet uses the VPN, but then I lose access to ssh, and webmin, and my other stuff that I would like to keep access to from, it does not need to be over the VPN, just accessible from the internet.

Is there a way through iptables to force use of an interface for certain protocols.?

---

### Post by SeijiSensei on 2012-12-11
> **Catalyph said:**
> I basically already have this working where everything leaving out to the internet uses the VPN, but then I lose access to ssh, and webmin, and my other stuff that I would like to keep access to from, it does not need to be over the VPN, just accessible from the internet.

Is there a way through iptables to force use of an interface for certain protocols.?

I'm not sure I entirely understand the problem.  Are you talking about inbound traffic to your machine over the Internet?  From where would you be accessing sshd and webmin, some other machine over the Internet?  

I think you might be able to handle this with port forwarding rules on the router upstream from the Linux box.  In iptables you can write a rule which [redirects]("http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO-5.html") traffic arriving on a specific port to another IP address.  I'm not sure that would help in your case, though.

---

### Post by The Cog on 2012-12-11
If you want to send different protocols in different directions, I think you need to set up different routing tables and mark packets as to which forwarding table they should use. Remember that you cannot allow traffic to the VPN end point to travel up the VPN itself so you will probably want a specific route to the VPN server over the internet, adn your default route to poimnt over the VPN. Something like this below shoud pick out SSH packets for special routing. (I've not trid it). Numbers 42 (the routing table number) and 99 (the firewall mark) are numbers I chose at random. 

```
# Make a new routing table with a different default route
ip route add default via 192.168.0.1 table 42

# Mark packets that need special routing
iptables -t mangle -A PREROUTING -p tcp --dport 22 -j MARK --set-mark 99

# Add a rule to use a differnt routing table for marked packets
ip rule add fwmark 99 table 42
```

---

### Post by Catalyph on 2012-12-11
> **The Cog said:**
> If you want to send different protocols in different directions, I think you need to set up different routing tables and mark packets as to which forwarding table they should use. Remember that you cannot allow traffic to the VPN end point to travel up the VPN itself so you will probably want a specific route to the VPN server over the internet, adn your default route to poimnt over the VPN. Something like this below shoud pick out SSH packets for special routing. (I've not trid it). Numbers 42 (the routing table number) and 99 (the firewall mark) are numbers I chose at random. 
 
```
# Make a new routing table with a different default route
ip route add default via 192.168.0.1 table 42
 
# Mark packets that need special routing
iptables -t mangle -A PREROUTING -p tcp --dport 22 -j MARK --set-mark 99
 
# Add a rule to use a differnt routing table for marked packets
ip rule add fwmark 99 table 42
```
 
 
I will try this when I get home. But i have a feeling that packet marking is not working. is there something I have to enable for it to work ? I think i tried this and it did not work properly or at all.
I think it came down to a kernel config option that was not enabled or existing. (UBUNTU 12.10)
MORE INFO:
 
I have DynDNS to my router (Public none VPN IP Address) 
so when i ssh i use the Dynddns address which goes to my router, which in turn forwards the port 22 traffic to the Ubuntu Server.
 
When i Start my VPN connection, I dont get the same address everytime.
 
I want to be able to have my machine use a VPN for everything except port 22, so I can SSH into the box from the internet using my dyndns address.
 
If the VPN is up, I cant because the default route is the VPN connection and the incoming traffic is not from the VPN, It comes in through the router and into Eth0 but then tries to go out the VPN interface.
 
If I can make a rule that says 
Traffic coming in from eth0 or 192.168.0.X on port 22 then responding outbound traffic will also go out on that interface and gateway.

---

### Post by SeijiSensei on 2012-12-11
If the router masquerades the port-forwarded traffic with its own internal address, say 192.168.0.1, you might try simply adding a specific route to that host:
```
/sbin/ip route add 192.168.0.1/32 dev eth0
```
That might be sufficient, but only empirical testing will tell.

---

### Post by The Cog on 2012-12-11
Hmm, I'm having difficulty finding good documentation on iptables and which filter tables can be used when. But I don't think output packets from the local PC actually pass through the PREROUTING table. I'll try to find out more.

---

### Post by Catalyph on 2012-12-11
> **SeijiSensei said:**
> If the router masquerades the port-forwarded traffic with its own internal address, say 192.168.0.1, you might try simply adding a specific route to that host:
```
/sbin/ip route add 192.168.0.1/32 dev eth0
```
That might be sufficient, but only empirical testing will tell.
 
 
My home router (D-Link) has a virtual server setting that can pass Outside port to aa specific IP and Port on the internal Network.But i have it set to simply take any inbound (from internet) traffic with port 22 to forward directly to the Ubuntu Box on port 22. So just a basic port forward.
 
```
/sbin/ip route add 192.168.0.1/32 dev eth0
```
 
So I guess this is saying add a route to host 192.168.0.1 via eth0? This is already working with the VPN
 
When my VPN is up all internal network traffic work fine and ssh is working but only on the internal network, if i turn the VPN off , everything work on internal and on internet.
Because the Default route changes on the Ubuntu machine when i turn on the VPN (Which I want) 
I only want to be able to specify some ports that can bypass the vpn

---

### Post by Catalyph on 2012-12-11
I think I found what I Need at this link.
But i dont know if my VPN Network IP will always be the same. so maybe i can script something.
 
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

---

### Post by The Cog on 2012-12-11
OK, Got it. This works - I verified with tcpdump that I can change the next-hop MAC address the packets are sent to:
```
# Make a new routing table with a different default route
ip route add default via 192.168.0.1 table 42
 
# Mark packets that need special routing
iptables -t mangle -A OUTPUT -p tcp --dport 22 -j MARK --set-mark 99
 
# Add a rule to use a different routing table for marked packets
ip rule add fwmark 99 table 42
```

P.S. Here's a good referemce: [http://lartc.org/](http://lartc.org/)

---

### Post by Catalyph on 2012-12-11
> **The Cog said:**
> OK, Got it. This works - I verified with tcpdump that I can change the next-hop MAC address the packets are sent to:
```
# Make a new routing table with a different default route
ip route add default via 192.168.0.1 table 42
 
# Mark packets that need special routing
iptables -t mangle -A OUTPUT -p tcp --dport 22 -j MARK --set-mark 99
 
# Add a rule to use a different routing table for marked packets
ip rule add fwmark 99 table 42
```
 
Awesome! Thank you for verifying Cog.
I will try this as soon as im at home!

---

### Post by Catalyph on 2012-12-11
neither one of these worked.

The ppp0 vpn connection is still blocking the ssh connection..

---

### Post by The Cog on 2012-12-12
There must be something else going on. Can you run 
sudo tcpdump -eni any tcp port 22
while you try to connect the SSH, voth with and without the VPN running, and post the output?

---

