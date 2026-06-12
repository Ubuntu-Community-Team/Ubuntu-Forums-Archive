---
title: "Why does my router have no default route?"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2013-06-22
I run a linux distro called Astaro on a machine at home that acts as my router. It's nothing too complicated - it just runs NAT, a DHCP server for my internal network, and a firewall. The strange thing that I just noticed is that when I ssh into it and run:

```
# route -n
OR
# ip route
```

neither show it having a default route. The only thing I see is my internal subnet, 127.0.0.1 on the loopback interface, and the network the router's external interface is on (a /22 subnet). How does the router know what interface to send out packets if I want to reach 8.8.8.8 for example? I always thought that if it didn't have a specific route in its routing table to send a packet to, it sent it out the default route, and if there is no default route, it drops the packet. How does my router work without a default route?

---

### Post by sanderj on 2013-06-22
What is your output of "route -n" and/or "ip route show"?

What is the output of "mtr -nrc2 8.8.8.8"

---

### Post by terminator14 on 2013-06-22
```
astaro:/root # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
96.41.15.0      0.0.0.0         255.255.252.0   U     0      0        0 eth2
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

astaro:/root # ip route show
96.41.15.0/22 dev eth2  proto kernel  scope link  src 96.41.15.94 
127.0.0.0/8 dev lo  scope link 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.1 

```

The program "mtr" is not installed on the distribution, and since the distribution is specifically made to be run on routers (as opposed to a regular desktop or server distribution), it comes with no package manager or compiler to add tools that are not pre-installed.

---

### Post by terminator14 on 2013-06-22
I take it from the lack of responses to such a basic networking question (despite about 90 views at the time of this writing) that I'm not crazy, and that a default route does work the way I described it earlier, and that this case is indeed weird?

---

### Post by capscrew on 2013-06-22
> **terminator14 said:**
> I take it from the lack of responses to such a basic networking question (despite about 90 views at the time of this writing) that I'm not crazy, and that a default route does work the way I described it earlier, and that this case is indeed weird?
The CoC for this forum is "bump only once every 24 hours".  Not everyone is on your timetable or in your timezone.

Have you considered what a default gateway really is?  If your router *is the gateway* to your ISP then what other route you have for a packet arriving on eth1 or eth2?  If this is Linux, IPTables is in control here.

What do you think this means ```
96.41.15.0      0.0.0.0         255.255.252.0   U     0      0        0 eth2
```

See [[COLOR="#FF8C00"]**here**[/COLOR]]("http://www.cyberciti.biz/faq/linux-unix-osx-bsd-windows-0-0-0-0-network-address/") for a helpful hint.

---

### Post by terminator14 on 2013-06-23
> **capscrew said:**
> The CoC for this forum is "bump only once every 24 hours".  Not everyone is on your timetable or in your timezone.

I've actually been on this forum longer than you, but thanks for the lesson...

> **capscrew said:**
> Have you considered what a default gateway really is?

That's basically the topic of this thread...

> **capscrew said:**
> If your router *is the gateway* to your ISP then what other route you have for a packet arriving on eth1 or eth2?

The day computers get smart enough to think for themselves, I will consider this possibility. Until that day, I will assume that a computer needs to be told in some way, shape, or form, what to do, even if there is only one option.

> **capscrew said:**
> If this is Linux, IPTables is in control here.

I actually hadn't considered that. I think this might be what is happening, for security reasons. Thank you.

> **capscrew said:**
> What do you think this means ```
96.41.15.0      0.0.0.0         255.255.252.0   U     0      0        0 eth2
```

See [[COLOR="#FF8C00"]**here**[/COLOR]]("http://www.cyberciti.biz/faq/linux-unix-osx-bsd-windows-0-0-0-0-network-address/") for a helpful hint.

That literally means: If any packets are destined for any IP between 96.41.12.1 and 96.41.15.254, look for the destination on eth2 using ARP. It has nothing to do with a default route, and unless that range of IP's encompasses the entire Internet (Hint: it does not), I don't think that helps much. A packet destined for, say, 8.8.8.8, is not part of that network, and will NOT apply to that route.

---

### Post by capscrew on 2013-06-23
> **terminator14 said:**
> I've actually been on this forum longer than you, but thanks for the lesson...

Then you should have known.> 

The day computers get smart enough to think for themselves, I will consider this possibility. Until that day, I will assume that a computer needs to be told in some way, shape, or form, what to do, even if there is only one option.

If they have dynamic routing the they do think for themselves.  Although I doubt a basic Linux based router does this.
> 

I actually hadn't considered that. I think this might be what is happening, for security reasons. Thank you.



That literally means: If any packets are destined for any IP between 96.41.12.1 and 96.41.15.254, look for the destination on eth2 using ARP. It has nothing to do with a default route, and unless that range of IP's encompasses the entire Internet (Hint: it does not), I don't think that helps much. A packet destined for, say, 8.8.8.8, is not part of that network, and will NOT apply to that route.

I would think it sends all packets to the next hop.

---

### Post by terminator14 on 2013-06-23
> **capscrew said:**
> Then you should have known. 

Unlike a computer, I have a brain and am able to think for myself, and my brain told me that out of the 90 people who had seen my original post, it is likely that:

[LIST]
[*]Some visitors had been searching for something else on a search engine, clicked the link to my thread, realized that it wasn't what they were searching for, and left immediately. Let's say 50% of those 90 fall into this category.
[*]The other 45 visitors either opened my thread out of curiosity, presumably because they know what a default route is, or because they genuinely wanted to help (again - they can't help if they don't know what I'm talking about, so I think it's safe to assume these people also know what a default route is).
[*]Let's also assume that half of those people don't have the 15 seconds it takes to reply "a default route is not the only way a router decides where to send a packet when it doesn't match any other route. See [URL]".
[/LIST]

So that leaves us with 22 visitors that have the knowledge to have pointed me in the right direction, and the time to tell me. Even if my already ridiculous over-estimations are wrong, and 10 times fewer people had the knowledge and/or time to tell me what I wanted to know, that's still leaves 2 people that could have told me. Based on this information, I made the assumption that no one left a reply because I was right, and that the problem was more complicated than me misunderstanding some basic networking concept. 

But, you know, the Coc is cool too...

> **capscrew said:**
> I would think it sends all packets to the next hop.

The next hop router is determined by the routing table. The packets we are talking about do not apply to any of the routes in the routing table. As far as I know, routers do not randomly pick an IP to be the next hop router in such cases.

I think your original answer might have been right, and my firewall is actually using iptables to decide which packets get to go to the default route (by sending them to the IP of the default route directly), and which ones don't. I'm not 100% sure on this, but I accept it as a possibility, and know that unless I want to read up on iptables to figure out exactly what each one of the 160+ rules in my router's iptables does, I should accept the answer - at least while everything works.

---

