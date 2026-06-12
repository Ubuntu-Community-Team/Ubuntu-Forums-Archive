---
title: "Server 12.04 - Secondary IP won't route outside of local network"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by jameswatson3 on 2013-03-12
I am using Ubuntu 12.04 as the platform for a VirtualMin installation which will host multiple websites for the same organization. For this, I need to bind multiple IP addresses in the same subnet to the server and I am having problems doing so.

I can bind the extra addresses either by using additional virtual nics (it is a vm) or by using virtual interfaces of one nic. In both cases the additional addresses ping just fine from any host on the local network, but only the primary nic can be pinged from any remote network. The behavior is just like what would happen if you configured a single nic with no gateway so I imagine this is an issue with the routing table, but I just can't produce a working config. Can anyone please take a look at my config and possibly point me in the right direction?

/etc/network/interfaces
```
# The loopback network interface
auto lo eth0 eth0:0
iface lo inet loopback


# The primary network interface
iface eth0 inet static
        address 10.192.3.104
        netmask 255.255.224.0
        gateway 10.192.0.1
        broadcast 10.192.31.255
        network 10.192.0.0
        dns-nameservers 10.192.0.210 10.192.0.198 127.0.0.1


iface eth0:0 inet static
        address 10.192.30.52
        netmask 255.255.224.0

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.192.0.1      0.0.0.0         UG    100    0        0 eth0
10.192.0.0      0.0.0.0         255.255.224.0   U     0      0        0 eth0

```

---

### Post by SeijiSensei on 2013-03-12
I suspect the problem has to do with the upstream router.  How do external hosts see this machine?  Port forwarding?  Are there rules for both addresses?

---

### Post by The Cog on 2013-03-12
What you have there looks OK to me - I can't think of anything missing. That makes me wonder of there's something else that's been overlooked, and I can think of two possibilities. 

Firstly, firewall. Do you have a firewall running on the server? Try the command
```
sudo iptables -nvL
```

Secondly, are you doing NAT on your router? If so, do you have port forwarding for the other addresses configured?

Finally, I would use tcpdump to capture traffic on the server while you try and contact it from off-net. This will show if the server is even being reached, and how it responds.
```
sudo tcpdump -en
```

---

### Post by jameswatson3 on 2013-03-12
Wow, thanks for the fast responses. The "external network" in question here is really just a different internal network for a remote site, so I don't think there is any nat'ing or port forwarding type configuration until you leave the organization network through the external firewall. I'm just testing access between two internal vlans. I'm not sure if it is an accurate test because of the way different platforms handle things, but for example a Windows server can add a secondary ip address and immediately communicate in the way that my Ubuntu server can't on the exact same networks. This is just another reason that I don't suspect the networking configuration, but am looking at the server side.

I did check firewall and showed no iptables rules.

My next step is to verify with a system that has never had the VirtualMin install that I was going to be using and will report back on that.

Any other suggestions?

---

### Post by jameswatson3 on 2013-03-12
Unfortunately my condition exists on out of the box ubuntu 12.04 install. I don't do anything but configure the network to get the behavior.

I did take your advice and capture network traffic using tcpdump. The ping definitely arrives at the server but appears to be simply dropped at that point. I've attached the dump of a ping to the ...138 (successful) and ...185 (unsuccessful) addresses.

```
16:10:08.149550  In 00:1f:27:40:04:00 ethertype IPv4 (0x0800), length 100: 10.1.0.200 > 10.192.10.138: ICMP echo request, id 64546, seq 6, length 64
16:10:08.149571 Out 00:50:56:be:0a:89 ethertype IPv4 (0x0800), length 100: 10.192.10.138 > 10.1.0.200: ICMP echo reply, id 64546, seq 6, length 64
16:10:09.145736  In 00:1f:27:40:04:00 ethertype IPv4 (0x0800), length 100: 10.1.0.200 > 10.192.10.138: ICMP echo request, id 64546, seq 7, length 64
16:10:09.145759 Out 00:50:56:be:0a:89 ethertype IPv4 (0x0800), length 100: 10.192.10.138 > 10.1.0.200: ICMP echo reply, id 64546, seq 7, length 64
16:10:38.055885  In 00:1f:27:40:04:00 ethertype IPv4 (0x0800), length 100: 10.1.0.200 > 10.192.10.185: ICMP echo request, id 12835, seq 1, length 64
16:10:39.055943  In 00:1f:27:40:04:00 ethertype IPv4 (0x0800), length 100: 10.1.0.200 > 10.192.10.185: ICMP echo request, id 12835, seq 2, length 64
16:10:40.056085  In 00:1f:27:40:04:00 ethertype IPv4 (0x0800), length 100: 10.1.0.200 > 10.192.10.185: ICMP echo request, id 12835, seq 3, length 64

```

Where to go from here?

---

### Post by The Cog on 2013-03-13
That seems strange. 
I can't easily test that arrangement here as I can't get a logon to a remote box to ping my PC. But I can ping other networks from my PC, and I can do so using secondary addresses, like this:
```
ifconfig eth0:0 172.16.7.222/24
ping -I 172.16.7.222 10.0.0.1
```
This ping works, and I can see with tcpdump in a different window that the secondary address is being used.
I wonder if trying this in your case might show some error message, such as network unreachable. 

I notice that the addresses in your trace don't match the ones in your first post.
The output from these two commands might shed some more light:
```
ip -4 addr list
ip -4 route list
```

---

### Post by SeijiSensei on 2013-03-13
Usually problems like these arise when the routing tables are not properly configured.  Are you sure the router for subnet A knows to pass traffic for subnet B to subnet B's router and vice versa?

---

### Post by The Cog on 2013-03-13
I don't think that's the case. Tcpdump shows that the server does indeed know how to send reply packets to the remote PC - we see it responding, so the routing is not the issue. The issue appears to be inside the server - the PC that tcpdump is being run on.

---

### Post by jameswatson3 on 2013-03-14
Latest observations:

After leaving a new virtual interface in place overnight, the address starts replying to pings the next morning. I've now done this two nights in a row with two new addresses, all on the same subnet.

However, as observed earlier, this behavior does not occur on a Windows server when the same steps are performed. I was about to set up a CentOS box to test its behavior, but have not done so yet.

So I'm thinking that this behavior must reflect some peculiarity of how Ubuntu handles networking combined with some kind of networking configuration on our part. (And to answer the earlier question, no I'm not "sure" of anything regarding our network configuration beyond the basics).

So in a sense, it is "working" but I'm not sure how brittle it might be. You guys have been so helpful. Before we consider this question answered, what do you make of this latest observation? What additional debugging steps would you take if in my shoes? What would you ask of your network administrator about this behavior?

Thanks so much.

---

### Post by fongmh on 2013-03-15
I had the same problem as you, but recently solved it by fixing the NAT rules on iptables. I had the same problem where my secondary IP kept pinging around the server but just couldn't get out. The instructions here really helped:

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

