---
title: "iptables is too smart for my own good"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by michealPW on 2008-12-08
Hi, everybody!

I can chat and join other games fine, but I cannot host my own games on Battle.net using StarCraft on Ubuntu 8.04.1.

Using Firestarter, I created a rule to allow incomming UDP data on port 6112 for StarCraft's Battle.net gaming service. This is what StarCraft manual recommends and I have past experience with Windows' firewalls with such a setup.

The problem appears to be the way Battle.net works.

So, you start StarCraft.exe and connect to battle.net. At this point, I have an established TCP/IP connection to the Battle.net server and I can chat. So, when I click on Games I get a list of games, can double-click on them and it joins and I can play fine. However, I think the way it works behind the scenes is the Games list is simply a list of StarCraft.exe hosts. When I double-click on them, StarCraft.exe then uses UDP/IP to send/recieve game data between that hosts' StarCraft.exe. I think all outbound data is allowed, by default.

The problem appears when I try to host a game, I think, because it's as though random people are sending data to port 6112, heading to my StarCraft.exe. Since they have no established state, they're being dropped. That's the design of Battle.net, it's mainly just a list of hosts and a chat relay.

I'm sorry for so much talking, I wanted to be clear about my problem and what I've done so far to try and fix it hehe!

Could anyone explain how to modify my rule to allow stateless UDP data to come into port 6112? I suppose Firestarter will not be useable in this case, I'll have to use the iptables?

---

### Post by ilrudie on 2008-12-08
To me this seams more like a port forwarding issue on your local router than anything else.  Do you have a router?  Is port forwarding configured?

---

### Post by jonobr on 2008-12-08
Hello


Doing a quick google , I put in battle.net and port number, and it brought me to the battlenet website.
On their site it said to allow 6112 for both TCP and UDP.
In and out, 

Have you tried that.

If that did not work, maybe try going to your ubuntu machine and open a console and monitor if the 6112 traffic makes it though.

You can do that by doing sudo tcpdump -i eth0 -v port 6112

If you see no traffic then you have a firewall blocking isse

---

### Post by michealPW on 2008-12-10
Thanks for the replies, everyone.

Maybe I should have stated this more clearly in my original post, but, I do *not* have a router and I *have* used Firestarter to disable the firewall to workaround the issue, this is currently how I host games.

The problem *is* the firewall, which *does* have a rule to forward both UDP and TCP data on port 6112, however, I still cannot host games while it's enabled.

The problem is that as users attempt to join my game, their StarCraft.exe will send a UDP packet to port 6112 --unsolicited-- to gage my network's responsiveness. The firewall drops this packet and they get a "latency too high error" and cannot join my game.

I'm *certain* this is the firewall, which cannot associate their initial packet to the exchange that had already occured between StarCraft.exe and the battle.net server on port 6112 and drops it as unsolicited or stateless right?

My question is how can I create or modify the existing rule to prevent this behavior for port 6112?

Thank you.

---

### Post by jonobr on 2008-12-10
Oki,
Yep I misunderstood your problem and underestimated your knowledge
Apologies for both :?
Doing some looking around, I did find some posts about firestarter and IP tables, which I am sure you reviewed already, and Im guessing you went to shields up to see your issue with the unsolicited packets

[http://ubuntuforums.org/showthread.php?t=571942](http://ubuntuforums.org/showthread.php?t=571942)

---

### Post by ilrudie on 2008-12-10
[UDP]("http://en.wikipedia.org/wiki/User_Datagram_Protocol") is always "stateless".  It is one way fire and forget communication.

Perhaps it would be best to show us the rules you have in place,

---

### Post by michealPW on 2008-12-10
I apologize for the lack of information in my original post. Here's where I am and how I got here...

I run StarCraft v1.16 in a Swedish Windows XP SP3 guest "inside" VirtualBox v2.0.6 on my Ubuntu v8.04.1 host system. On the host Ubuntu system, I've installed Firestarter v1.0.3-6ubuntu3 to setup the linux firewall.

I've performed a lot of tests and have isolated the problem down to the Linux firewall. I can host games normally simply by using Firestarter to "stop" the firewall.

**[Here's](http://rafb.net/p/s5lusF79.html)** the output I get from

```
sudo iptables -nL > ~/tables
```

I've also attached it to this post. The two rules I added using Firestarter are:

```

ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:6112
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:6112

```

I apologize if I've left anything out, thanks a lot for your time so far.

---

### Post by ilrudie on 2008-12-11
I did not realize virtual box was involved.  How is the the VMs networking configured?  Is it NAT or HIN?  VirtualBox NAT has unreliable UDP support according to the VirtualBox user manual.

A common model for building something like this would be to bridge the VMs interface to a physical interface on the host.  Give the VM a routable IP and let it act like a physical box.  You don't have a router you said but can you get a second IP from your ISP?  If you can you can use your ISPs router instead of buying one or creating a router with iptables in the host.

---

### Post by michealPW on 2008-12-13
Hi, ilrudie. Thanks a lot for your time!

You're right, I'm using NAT to connect the VM to the host's network. However, it's all 1 machine and after testing I am confident the NAT bridge isn't the culprit.

Basically, I ran Firestarter and disabled the Firewall, then startup the VM/Windows/StarCraft and can host games 'till the sun comes up next morning. This is why I'm so confident it's a problem with the Netfilter firewall, however I simply lack the knowledge to fix it.

Does anyone know of a good book on the iptables utility? Perhaps my problem is this Firestarter program?

---

### Post by ilrudie on 2008-12-13
Try [this]("http://tldp.org/LDP/nag2/") or [this]("http://www.tldp.org/LDP/LGNET/103/odonovan.html").  TLDP usually has pretty good stuff.

---

### Post by michealPW on 2008-12-14
ilrudie

Thanks a lot for the recommendation. I'm quite busy today, but tomorrow I'll have some time I can spend on reading it.

Thanks again for all your time and effort, it's highly appreciated. Once I understand this more, I'll edit my original post with [Solved] and directions on how I managed to do it.

Further direction's still welcome until then, however, so don't be shy:)

---

