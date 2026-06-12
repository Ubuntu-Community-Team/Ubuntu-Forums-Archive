---
title: "Ubuntu cross-domain internet sharing issue"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by NDWolfwood5268 on 2009-06-19
I spent around... I'd say 17 hours working on this? I'm not a great server guy, but I'm somewhat well versed in Ubuntu and thought that an Ubuntu Firewall would help us replace our current dying firewall. The Firewall is responsible for sharing internet across two domains.

We have two domain addresses for two separate LANs. First LAN for the main office of 6 computers is a 90.0.0.x domain. The second is a set of servers on a 100.0.0.x domain. 

In my current setup: The firewall can see everything; both domains and the internet. The 90 domain can see the 100 domain. The 100 domain can see the 90. The 90 and 100 domains CANNOT see the internet.

I've tried bridges through bridge-utils, which kills all connections, I've tried FWBuilder, I've tried Firestarter, and I've tried some how-tos on configuring forwarding with iptables.

All of them fail and usually take a step back in elliminating the connection across domains that I had. 

Does anyone have ANY suggestions please? This is driving me nuts.

The computer is running 9.04 server i386 with Gnome on a custom built PC with 2 NICs and one integrated Ethernet controller.

Thanks in advance!
:popcorn:

NOTE: I find it odd that the domains can all communicate fine without a bridge or anything... I just plugged them in and told them to look at the firewalls IP for a gateway. All how-to's say that it should require a bridge of some sort; I have none...

---

### Post by NDWolfwood5268 on 2009-06-19
No one has any input? Please? I'm really stuck and I'll probably be staying late tonight again to work this one out...

---

### Post by jonobr on 2009-06-19
Im not sure I can help, but if you could jot down a quick network diagram of what you are trying to do it may help people....

Im reckoning your old setup was working ?

How did that connect the two domains?

Are these in two geographical locations?
If yes, how are they currently connected, is it using some form of leased line?

Have you tried using traceroute or ping to figure our where your packets are going or not going?

Are you familiar with using wireshark or tcpdump?
scould you grab traces of whats working and whats not?

Also results from netstat -rn may show routing info that may help figure where pacekts are going or not going


Again, a network diagram showing interfaces may help

---

### Post by usererror on 2009-06-19
whoa isn't the 90.x.x.x and 100.x.x.x in the public IP range?  You should be using a subnet that is private, not in the public IP range...  

[http://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses](http://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses)

Also if you've got one firewall for two networks I'd recommend using IPCOP.  Throw in a total of three NICs and use one for the WAN, one for the first local network and the third card for the 2nd local network.

I'd be curious to see a traceroute to a public IP address (like one of your DNS servers from your ISP.

This is also a good "map" [http://xkcd.com/195/](http://xkcd.com/195/)

---

### Post by jonobr on 2009-06-19
Hello


From the initial post it sounds as if this is a drop in replacement for something that is working, 

NDWolfwood5268 can your confirm that?

are your certain these addresses were already in use and are golden?

---

### Post by NDWolfwood5268 on 2009-06-19
> **jonobr said:**
> Hello


From the initial post it sounds as if this is a drop in replacement for something that is working, 

NDWolfwood5268 can your confirm that?

are your certain these addresses were already in use and are golden?

Thanks for replying guys!

Quite. We HAVE a 'working' firewall that, quite sadly, has developed cancer. It's old, the software isn't supported, and it needs to be decomissioned. The IP addresses are perfectly fine, at least in that they have worked in the past and I'm posting this reply using a computer on the 90 domain in the same configuration I want to replicate.

I'll post a diagram in a few when I make it, but for a quick rundown: We were using Kerio WinRoute firewall to manage policies and connections over this network. The firewall has 3 NICs in it (one being an integrated controller in this case with the Motherboard) that each coordinate to the internet (eth0), the 100's (eth1), and the 90's (eth2). 

I haven't used incredibly elegant debug methods, mostly because I'm not a networker so I'm doing what I know, pings and routing table outputs. 

One thing my coworker showed me was a package or two was missing that was recommended from a tutorial. I installed them but can't test til 5:00 today (it's 2:43 right now here). My faith is shaky though, it's just one more approach on the pile.

---

### Post by usererror on 2009-06-19
Are you using DHCP from your ISP for your WAN interface?  Or static?  What is it's subnet?  Just the first two octets.

Again, I can't figure out how your original setup if your IP scheming is using internet ip addresses, maybe the new firewall is 'smarter'. :)

---

### Post by jonobr on 2009-06-19
In addition to the diagram,
could you share the results of the ifconfig from a terminal window (if its not confidential info)

This will show the subnets your using etc.

Also, AFAIK if you have two separate subnets you will not be able to bridge
as bridge occurs between two lan segment in the same subnet.

If you have to seperate network subnets , you will need to route between the two,

eitherway, the ifconfig will show this information

---

### Post by NDWolfwood5268 on 2009-06-19
Ok, as promised, here is my network diagram. I'm not that great with Visio, so sorry if it sucks. The point should be illustrated I think.

As you can see, I have two separate 'LAN's, I guess, and each can see each other over our firewall. Talking about our old configuration, this was done on a Windows 2000 machine with WinRoute firewall. It was the gateway through which internet access was achieved.

In our new configuration, the Ubuntu server will have a firewall policy installed, but for now, I just want internet. It can communicate on both domains and each domain's members can access each other. Basically, it already works 90% except only the Ubuntu 'firewall' server has internet, not the individual members of each network.

Also, maybe of note, this Ubuntu server is meant to be temporary while we get the Windows box upgraded at the request of the boss. At least that was the plan, to get a more stable Firewall then the 2000 machine so we can reinstall 2003 on the Windows box with a new firewall. So I'd take the spit and duck tape solution if there is one right now. As is we're looking at more asinine options unless we can get Ubuntu up. Such as working on the weekend.

---

### Post by jonobr on 2009-06-19
Blank doc chief,,,,,
Could you try that again.....
Nothing fancy, just quick and dirty and the output of ifconfig

---

### Post by usererror on 2009-06-19
Post a traceroute from one of you 100.x.x.x servers or 90.x.x.x on your existing setup you need to replace.  If I do a ping to 90.0.0.10 it resolves to a server in France...unless that's one of your user's work stations. ;)

---

### Post by NDWolfwood5268 on 2009-06-19
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto lo
# iface lo inet loopback

# The primary network interface

# iface eth2 inet static
# address 100.0.0.50
# netmask 255.0.0.0

# auto eth2

# iface eth1 inet static
# address 90.0.0.50
# netmask 255.0.0.0

# auto eth1

# iface eth0 inet static
# address 66.160.122.66
# netmask 255.255.255.248
# gateway 66.160.122.65

# auto eth0

This is the interfaces document I have. The settings are true to what we have here. Also, no, we won't be using DHCP, it's all static. 

Let me know if I'm missing anything else.

Also, I remedied that document muck up of mine, so view away!

---

### Post by NDWolfwood5268 on 2009-06-19
> **usererror said:**
> Post a traceroute from one of you 100.x.x.x servers or 90.x.x.x on your existing setup you need to replace.  If I do a ping to 90.0.0.10 it resolves to a server in France...unless that's one of your user's work stations. ;)

No no no no. Those domains are INTERNAL. Our external IP's are different. These are for internal use. We made them up.

Yeah....

EDIT: And yeah, didn't know that about the subnets... we tried to keep them the same anywho though, but we'll double and triple check our settings when we start the testing again today. We're not allowed to play with it til after hours so the office doesn't lose internet.

---

### Post by jonobr on 2009-06-19
Thanks for posting the visio, you put a lot of work into that!!
also thanks for the ifconfig

I see your using a class a network.
Not a problem as far as I can tell , it just allows for a huge.... amount of hosts,

So not, if you could walk me through this again. the 90 subnet can ping the 100.
the 100 hosts can ping the 90

the 90 hosts can ping the eth0 of the ubuntu box, correct?

the 100 can ping the eth0 of the ubuntu box.

can both ping the default gateway?

Sorry if we are redoing this again , I need to get this straight in my head.,..

---

### Post by jonobr on 2009-06-19
Additionally, how are they at pinging 66.160.122.65?

Can they do that?

Coould you also double check the subnetting of your old network.
are you sure they were a class A address?

---

### Post by NDWolfwood5268 on 2009-06-19
> **jonobr said:**
> Additionally, how are they at pinging 66.160.122.65?

Can they do that?

Coould you also double check the subnetting of your old network.
are you sure they were a class A address?

No, that's what we WANT. What we currently have (and want to recreate with linux) is having the 90's and 100's ping the Firewall (which will have an IP on each domain) and use it as the default gateway. The firewall then fowards their internet reqeusts to the internet gateway (that 66.x.x.x address).

Currently, you are all correct EXCEPT the 90's and 100's CANNOT ping the firewall OR the internet (which they shouldn't, they should see the firewall and the firewall would forward requests).

Does that make sense? Otherwise, yes, the two ip ranges can ping each other AND the firewall. Just they aren't being forwarded I guess.

---

### Post by jonobr on 2009-06-19
Thanks for your patience with me clarifying the same questions over again.

The firewall and the ubuntu box are on the same box, correct?

I.e. you dont have a separate firewall external to the ubuntu box.
Are you using IP tables on the ubuntu box?

Im going to ask for a trace, but again, understanding whats what will help in figuring this.
Also confirming the old subnet structure will really help.

Lastly, can they ping 66.160.122.66 which is the eth0 of your server

---

### Post by NDWolfwood5268 on 2009-06-19
Idealy the other domains, 90 and 100, would not ping the 66 address, the address of our ISP. They would be directed to the Ubuntu box, which, btw, I've been calling 'firewall' out of habit. Our box is NAMED firewall for all intents and purposes just cause we're unimaginative hehe. So, yes, a firewall will be on the Ubuntu box, but that's a seperate thing I can do later, for now, the Firwall (aka, just the Ubuntu server itself) needs to be configured to route the requests to the internet, I guess is what we need. To be honest, I'm not sure what I need hehe, I just THINK I do.

And that routing stuff, how? I'm not too versed in network debugging on linux, only software really.

---

### Post by scrooge_74 on 2009-06-19
I'm no expert here, but I think you need to set the box as a proxy for all incoming traffic from your two lans and then they go out the door to the internet. Behind the prxy goes the firewall to protect your lans from would be crackers.

Maybe this link can help out is a bit old.

[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)

---

### Post by jonobr on 2009-06-19
UNderstood, however, ping is just letting us know how the box is routing.

When you tracert or ping it will will show you how its getting there and if things are configured correctly.

Im attaching two tracerts to your network just for giggles.
Interesting to note that your I can get to your 65 ip address
however, its not getting to your 66 IP address which is the next hop to your router.

It may be that ICMP may be blocked, or it could be that its not routing from your .65 to your .66

I am wondering if there is a possibility of getting on the 65 box and ping .66 to check thats ok?
and can you ping 66 to 65?

Also from a client try doing a traceroute from a client machine on 90 or 100 and see where it goes...
A ipconfig from one of those 90 or 100 clients may show something

SOrry for all the questions

---

### Post by jonobr on 2009-06-19
mmmmmm...........

Im seeing responses now from .65 and .66

Have you changed something?
Did you call the ISP and tell them they were routing your packets?

Is it working as it looks good from this end....

---

### Post by NDWolfwood5268 on 2009-06-19
Sorry, at 5:00 today our office left so that I can destroy our internet and play with it. I just configured the firewall as closely to what I want as possible, aka, the situation I had described. I'm now on it and posting from it. The other PC's can't see the web.

Note: the 65 machine is our gateway and it's merely a router is what I'm told. It's the gateway for this firewall computer and this firewall is supposed to be the gateway for the other computers. 

It looks like the route the 90 computer we're checking is using is it's getting to the Firewall pc fine, but no further.

Note: I tried to configure iptables and apparently was missing ipmasq and dnsmasq. Now that I installed them, if I restart, I cannot see any internet sites on the firewall computer. If I uninstall them, I get internet again.

Also, with them installed immediately after a reboot, I get an error pining the 90 and 100 domains. It says 'operation not permitted'. I think I mucked something up in settings.

I was trying to configure NAT and forwarding to the ISP gateway from this computer. That's what I think I ultimately need. If so, I'm fuzzy on how to do it.

---

### Post by jonobr on 2009-06-19
I think your biting off more then you can chew,

Your doing nat firewalls and routing all at the one time.,

If I were in your shoes, I would get the routing figured out, 
then once thats working, start hardening my system using iptables and then make whatever changes are required to get nat or whatever services working.

Your going to end up trying to fix multiple problems at once and not know if your coming or going

---

### Post by NDWolfwood5268 on 2009-06-19
Well, that's the thing. I thought iptables was seperate from a firewall. Again, for all intents and purposes 'Firewall' means the server I'm trying to configure to forward internet access. As for the actual firewall program or service, I'm not doing that right now and I think I can do that alone later.

For routing, what would you recommend? I thought it was achieved through iptables, but I think you said that's incorrect?

---

### Post by jonobr on 2009-06-19
ok, lets start over, 

you want to go from 90 or 100 to the default gateway....

do a ping from the 100 an/or 90

whilst running the following command

```
sudo tcpdump -vvXns0 -i eth0 proto ICMP
```

Post the results here

This will show us if packets are getting to the eth0 interface which is essnetially what your trying to do , correct?

Additional- IPtables allows you as an admin control the ip packets it recieves, whether it forwards them, drops them (like a firewall) or modifies them, eg convert port 80 to port 8080 and so on.
When you are doing NAT you will have to use it however as mentioned, you just seem to have basic routing problems at the moment,
getting packets from a to b

---

### Post by NDWolfwood5268 on 2009-06-19
Bah, nothing... just says 'listening' and that's it. I tried it on the eth0 (internet port) as well as the eth2 (from the 90's) and nothing. 

Note: I tried Firestarter firewall GUI while I was on my own. I was able to see a request from google coming in when a computer on the 90 domain tried to connect, but it seems to not have made it there to the computer. I OKed web traffic on it trying to get it through, and nothing. So Firestarter seemed to see stuff happening, but nothing succeed.

I was hoping to use Firestarter to at least bridge internet to one domain, if not both. The 90's are really what NEED internet, the 100's can live without it for the time being if they can be viewed within our office like they can be now.

---

### Post by jonobr on 2009-06-19
so when you ping from a client pc on the 90 network (which I think is on eth2)
 you ran
```
 tcpdump -vvXns0 -i eth2 proto ICMP 
```
and you saw nothing? 
Is that correct?

---

### Post by NDWolfwood5268 on 2009-06-19
tcpdump: listening on eth2, link-type EN10MB (Ethernet), capture size 65535 bytes
21:12:57.346332 IP (tos 0x0, ttl 128, id 23621, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 49155, length 40
    0x0000:  4500 003c 5c45 0000 8001 2a2d 5a00 001d  E..<\E....*-Z...
    0x0010:  5a00 0032 0800 8b58 0200 c003 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:12:57.348345 IP (tos 0x0, ttl 64, id 18905, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 49155, length 40
    0x0000:  4500 003c 49d9 0000 4001 7c99 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 9358 0200 c003 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:12:58.346868 IP (tos 0x0, ttl 128, id 23622, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 49411, length 40
    0x0000:  4500 003c 5c46 0000 8001 2a2c 5a00 001d  E..<\F....*,Z...
    0x0010:  5a00 0032 0800 8a58 0200 c103 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:12:58.346918 IP (tos 0x0, ttl 64, id 18906, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 49411, length 40
    0x0000:  4500 003c 49da 0000 4001 7c98 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 9258 0200 c103 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:12:59.347017 IP (tos 0x0, ttl 128, id 23623, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 49667, length 40
    0x0000:  4500 003c 5c47 0000 8001 2a2b 5a00 001d  E..<\G....*+Z...
    0x0010:  5a00 0032 0800 8958 0200 c203 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:12:59.347070 IP (tos 0x0, ttl 64, id 18907, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 49667, length 40
    0x0000:  4500 003c 49db 0000 4001 7c97 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 9158 0200 c203 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:00.347174 IP (tos 0x0, ttl 128, id 23624, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 49923, length 40
    0x0000:  4500 003c 5c48 0000 8001 2a2a 5a00 001d  E..<\H....**Z...
    0x0010:  5a00 0032 0800 8858 0200 c303 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:00.347227 IP (tos 0x0, ttl 64, id 18908, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 49923, length 40
    0x0000:  4500 003c 49dc 0000 4001 7c96 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 9058 0200 c303 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:01.347325 IP (tos 0x0, ttl 128, id 23628, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 50179, length 40
    0x0000:  4500 003c 5c4c 0000 8001 2a26 5a00 001d  E..<\L....*&Z...
    0x0010:  5a00 0032 0800 8758 0200 c403 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:01.347378 IP (tos 0x0, ttl 64, id 18909, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 50179, length 40
    0x0000:  4500 003c 49dd 0000 4001 7c95 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 8f58 0200 c403 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:02.347477 IP (tos 0x0, ttl 128, id 23629, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 50435, length 40
    0x0000:  4500 003c 5c4d 0000 8001 2a25 5a00 001d  E..<\M....*%Z...
    0x0010:  5a00 0032 0800 8658 0200 c503 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:02.347532 IP (tos 0x0, ttl 64, id 18910, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 50435, length 40
    0x0000:  4500 003c 49de 0000 4001 7c94 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 8e58 0200 c503 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:03.347618 IP (tos 0x0, ttl 128, id 23630, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 50691, length 40
    0x0000:  4500 003c 5c4e 0000 8001 2a24 5a00 001d  E..<\N....*$Z...
    0x0010:  5a00 0032 0800 8558 0200 c603 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:03.347673 IP (tos 0x0, ttl 64, id 18911, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 50691, length 40
    0x0000:  4500 003c 49df 0000 4001 7c93 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 8d58 0200 c603 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:04.347764 IP (tos 0x0, ttl 128, id 23631, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 50947, length 40
    0x0000:  4500 003c 5c4f 0000 8001 2a23 5a00 001d  E..<\O....*#Z...
    0x0010:  5a00 0032 0800 8458 0200 c703 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:04.347816 IP (tos 0x0, ttl 64, id 18912, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 50947, length 40
    0x0000:  4500 003c 49e0 0000 4001 7c92 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 8c58 0200 c703 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:05.347924 IP (tos 0x0, ttl 128, id 23632, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 90.0.0.50: ICMP echo request, id 512, seq 51203, length 40
    0x0000:  4500 003c 5c50 0000 8001 2a22 5a00 001d  E..<\P....*"Z...
    0x0010:  5a00 0032 0800 8358 0200 c803 6162 6364  Z..2...X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:13:05.347978 IP (tos 0x0, ttl 64, id 18913, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.50 > 90.0.0.29: ICMP echo reply, id 512, seq 51203, length 40
    0x0000:  4500 003c 49e1 0000 4001 7c91 5a00 0032  E..<I...@.|.Z..2
    0x0010:  5a00 001d 0000 8b58 0200 c803 6162 6364  Z......X....abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi

I wasn't being pinged.

Sorry for the late response, we hit up red lobster here.

---

### Post by jonobr on 2009-06-19
That ping appears to be between two hosts on the 90 subnet 

namely

90.0.0.50 > 90.0.0.2


What you need to do is ping the gateway address .66 or .65 from something on the 90 address.

---

### Post by jonobr on 2009-06-19
also from everything Im seeing , I think you will end up needing to send the result of 

```
sysctl net.ipv4.ip_forward
```


its beginning to look as if you just have not enabled IP forwarding

I remember when you setup your new settings I could ping 66 and 65 wheres  all packets are not getting across the box

---

### Post by NDWolfwood5268 on 2009-06-19
ZOMG we have a breakthrough.

Yeah, the ip forwarding was partly it. I got an iptables gui so I can play with it a bit more intuitively (check repositories if your reading and looking) called knetfilter. With it we saw that forward, output, and input chain policies were set to 'DROP'. We set them to 'ACCEPT' and now the computers can somewhat see the internet. They can ping google and get a response but the response is 'dropped' on its way back.

NOTE: The ip configuration we have is that the 'Firewall' box that has Ubuntu on it has an ip on both domains (it's 100.0.0.50 and 90.0.0.50 on each). The default gateway SHOULD be set to these IP's on each domain respectively. We had it like that in the past, and it looks like it's relatively good now. We just needed to forward the requests through the Firewall box.

So, do you have any input on our new situation? Google fails when responding back?

---

### Post by NDWolfwood5268 on 2009-06-19
MP (1), length 60) 90.0.0.29 > 166.160.122.65: ICMP echo request, id 512, seq 13828, length 40
    0x0000:  4500 003c 5f76 0000 8001 604c 5a00 001d  E..<_v....`LZ...
    0x0010:  a6a0 7a41 0800 1558 0200 3604 6162 6364  ..zA...X..6.abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi
21:39:05.601571 IP (tos 0x0, ttl 128, id 24443, offset 0, flags [none], proto ICMP (1), length 60) 90.0.0.29 > 166.160.122.66: ICMP echo request, id 512, seq 14084, length 40
    0x0000:  4500 003c 5f7b 0000 8001 6046 5a00 001d  E..<_{....`FZ...
    0x0010:  a6a0 7a42 0800 1458 0200 3704 6162 6364  ..zB...X..7.abcd
    0x0020:  6566 6768 696a 6b6c 6d6e 6f70 7172 7374  efghijklmnopqrst
    0x0030:  7576 7761 6263 6465 6667 6869            uvwabcdefghi


Here's that output as requested. We pinged one each. Gonna give you one more set of output for that other request.

---

### Post by NDWolfwood5268 on 2009-06-19
net.ipv4.ip_forward = 1

Yeah, actually, I coulda just said that. I JUST modified that like 10 seconds ago hehe. That got us forwarded outside I think, but the return aspect is dropping it seems.

---

### Post by jonobr on 2009-06-19
Great minds and all that.

So when you say google fails coming back, do you know where its dropping the packets?

```
tcpdump -vvXns0 -i eth0 port 80
```

When you google You should see packets going to google and if you see a response its getting to eth0

you then need to change to the target subnets Ethernet interface

eg if the response is for eth2 type

```
tcpdump -vvXns0 -i eth2 port 80
```

If you dont see it there check eth1,. if you dont see it there its being lost in the box itself and you may need to add routes to the subnets in question, but do tcpdumps first

---

### Post by NDWolfwood5268 on 2009-06-19
EDIT: I forgot, we never set the 100's computer to have this Firewall box as a gateway hehe. Gonna do that now, but I expect it to mirror the 90's so I won't spam the results if you don't really need them. Getting one domain up should work for the other.

Ok, when accessing google from the 90 test computer, we get the first two. When accessing it from the 100 computer, which should be connected to eth1, we got nothing... That's fine though, I GUESS since we aren't REALLY concerned with the 100's. If the 90's are up, we'll be silver.

So, let me know if this helps. I'll be googling that routing bit you mentioned.

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
21:54:54.563937 IP (tos 0x0, ttl 127, id 24838, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2650 > 8.15.228.161.80: S, cksum 0x314f (correct), 3421779244:3421779244(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 6106 4000 7f06 53f4 5a00 001d  E..0a.@...S.Z...
    0x0010:  080f e4a1 0a5a 0050 cbf4 352c 0000 0000  .....Z.P..5,....
    0x0020:  7002 ffff 314f 0000 0204 04ec 0101 0402  p...1O..........
21:54:57.581366 IP (tos 0x0, ttl 127, id 24840, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2650 > 8.15.228.161.80: S, cksum 0x314f (correct), 3421779244:3421779244(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 6108 4000 7f06 53f2 5a00 001d  E..0a.@...S.Z...
    0x0010:  080f e4a1 0a5a 0050 cbf4 352c 0000 0000  .....Z.P..5,....
    0x0020:  7002 ffff 314f 0000 0204 04ec 0101 0402  p...1O..........
21:55:03.516684 IP (tos 0x0, ttl 127, id 24844, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2650 > 8.15.228.161.80: S, cksum 0x314f (correct), 3421779244:3421779244(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 610c 4000 7f06 53ee 5a00 001d  E..0a.@...S.Z...
    0x0010:  080f e4a1 0a5a 0050 cbf4 352c 0000 0000  .....Z.P..5,....
    0x0020:  7002 ffff 314f 0000 0204 04ec 0101 0402  p...1O..........
^Z
[9]+  Stopped                 tcpdump -vvXns0 -i eth0 port 80
root@Thor:~# tcpdump -vvXns0 -i eth2 port 80
tcpdump: listening on eth2, link-type EN10MB (Ethernet), capture size 65535 bytes
21:55:23.691337 IP (tos 0x0, ttl 128, id 24868, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2652 > 8.15.228.161.80: S, cksum 0x731e (correct), 3967013595:3967013595(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 6124 4000 8006 52d6 5a00 001d  E..0a$@...R.Z...
    0x0010:  080f e4a1 0a5c 0050 ec73 d2db 0000 0000  .....\.P.s......
    0x0020:  7002 ffff 731e 0000 0204 04ec 0101 0402  p...s...........
21:55:26.654271 IP (tos 0x0, ttl 128, id 24870, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2652 > 8.15.228.161.80: S, cksum 0x731e (correct), 3967013595:3967013595(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 6126 4000 8006 52d4 5a00 001d  E..0a&@...R.Z...
    0x0010:  080f e4a1 0a5c 0050 ec73 d2db 0000 0000  .....\.P.s......
    0x0020:  7002 ffff 731e 0000 0204 04ec 0101 0402  p...s...........
21:55:32.690332 IP (tos 0x0, ttl 128, id 24874, offset 0, flags [DF], proto TCP (6), length 48) 90.0.0.29.2652 > 8.15.228.161.80: S, cksum 0x731e (correct), 3967013595:3967013595(0) win 65535 <mss 1260,nop,nop,sackOK>
    0x0000:  4500 0030 612a 4000 8006 52d0 5a00 001d  E..0a*@...R.Z...
    0x0010:  080f e4a1 0a5c 0050 ec73 d2db 0000 0000  .....\.P.s......
    0x0020:  7002 ffff 731e 0000 0204 04ec 0101 0402  p...s...........
^Z
[10]+  Stopped                 tcpdump -vvXns0 -i eth2 port 80
root@Thor:~# tcpdump -vvXns0 -i eth1 port 80
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
^Z
[11]+  Stopped                 tcpdump -vvXns0 -i eth1 port 80

---

### Post by jonobr on 2009-06-19
could you do me a huge favour

run the trace again, this time as follow

```
sudo tcpdump -w trace.pcap -s 1600 -i any port 80
```

run a google from the 90 network,

then run a google from the 100

when thats done hit control c to stop the trace, you will have a file called trace.pcap
post the result here,
it will be so much easier to look at  with the -w switch on tcpdump......


When Im done Ill show you how I view the packets,
which will help you in your network montoring

---

### Post by NDWolfwood5268 on 2009-06-19
Hmm... I don't know what kind of dark magic you had me do, but I couldn't open, read, or upload the raw file so I added it to an archive and attached it. Hope that's good enough and I didn't muck it up...

---

### Post by jonobr on 2009-06-19
no,

no dark magic yet...
The -w switch just dumps it to a file that allows a package like wireshark read it and will decode it to hex and englsh readable. You can add wirehark from synaptic to view this
Im attaching a snap shot,.

See the packets marked in a red box?

That appears to be the ubuntu box accessing google and google responding.

See the packets in blue, they are the 90 machine accessing bing, they seem to be hitting the interface of the ubuntu box but dont appear to be going out.

Is this correct?

---

### Post by NDWolfwood5268 on 2009-06-19
Ok... I think I get you, so google receives us but it never makes it back? Because what we get here in the browser on the 90 machine is 'connection interrupted'. And that was when it was waiting for a response from google. So we THOUGHT that we were on the receiving end when it died.

Are we wrong? And do you have a recommendation of how to solve this thing? We've tried multiple bridging and how-to's this whole time and it's sounding like we made 0 headway...

---

### Post by jonobr on 2009-06-19
you know what

Im just after remembering something you mentioned.

You mentioned previously that all the addresses you are using (90 and 100) are all internal IP addresses and not real.

The problem you are going to have is that Im sure you were natting in your old environment.

The packets that you end up sending out from 90.x are going to be sent to the real 90.x address somewhere on the internet , not back to you.


Yhe addresses are going to have to be natted from the ubuntu box.

I havbe not set that up myself, but here is an excellent thread explaining how this is done.

[HERE]("http://ubuntuforums.org/showthread.php?t=111972")

---

### Post by jonobr on 2009-06-19
Let me explain a bit further...
to get to google, you need the ip address of the google server.

google receives the packet and then responds back to the source ip address sending the information.

It takes that source ip address and then uses that information in its reponse packets with the data to fill into your browser.

However, when it replies, the intenet knows better,
it does not want to route it back to you, it wants to route it back to the 90 address which belongs to some dude in france.

Nat or masquerading gets you out of this.

What happens is that the ubuntu box receives the packet from you 90 machine.
It changes the source IP address to the .66 address
it sends the packet, google responds to .66.
.66 knows this packet belongs to the 90.x address and modifies it and sends to 90.x

So Im thinking this is what your old network did.
and to replicate that you need to setup the nat on your machine.

Additionally, you recall at the start of this someone mentioned that those addresses are real.

The address that should be used for internal networking are defined in a standard which outlines network number.
Basically the same people who gave you your .66 address.

They define that private networks should use 192.168.x and 10.10.x.x address.
Thats why you see all home networking devices are 192.168 based

---

### Post by NDWolfwood5268 on 2009-06-19
Wow... much thanks dude, I just needed to get that Masquerade script, add my external IP, and I was good. It has some literature to read up on, but it's 11:08pm here and I'm ready to go home, so I'll get smart a bit later.

Thanks for your help, I am TRULY grateful. I'll keep those routing tricks marked

):P

---

### Post by jonobr on 2009-06-19
Excellent,

I forgot you were using the internals and not real ips,

The one thing I was going to warn you about in his script was

EXTIF="eth2"
INTIF="eth1"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 


In your setup your using extif as eth0 not eth2,

but it sounds as if you got that and are rocking and rolling...
One other point, you original network had ICMP response disabled,
this stops robots trying to discover network from getting you ip address. Your new network doesnt have this and responds to ping and traceroute.
I would recommend you modify your iptables to drop any incoming ICMP ping request, unless you want and need them

Anyway, sounds like you increased your usefulness to the company in these dark days

Have a good nights sleep

---

