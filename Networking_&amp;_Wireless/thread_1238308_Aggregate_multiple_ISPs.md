---
title: "Aggregate multiple ISPs"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by Ellixis on 2009-08-12
Hi,

I want to aggregate (not load-balance) multiples (in my case 3) xDSL lines (all differents ISPs) on my linux router.

PC Linux Router (in our office) with 4 NICs cards :
- **eth0** (LAN : 192.168.0.0/24) connected to a simple switch
- **eth1** connected to ISP1 (15 Mbps)
- **eth2** connected to ISP2 (15 Mbps)
- **eth3** connected to ISP3 (30 Mbps)

eth1, eth2 and eth3 have their own IP & Gateway; all different.

I know that I can load-balance using *iproute* or *iptables*, but this is not what I'm looking for.
I also know that I can use *MLPPP*, but the ISPs need to support it, so it's not a solution for me.

What I'm looking for is aggregate the links of our 3 ISPs (15+15+30= 60 Mbps !!) through a server in a datacenter (with a big Internet pipe : >100 Mbps). The way to achieve this would be to :
[list=1]
[*]Make 3 VPN connections (1 for each ISP) from our Linux router to our **Datacenter' Server** 
[*]Bond these 3 VPN connection using "Linux Ethernet Bonding" (**ifenslave** package), resulting in a new bond0 interface
[*]Configure our linux router to use **bond0** to access Internet (create a new route ?)
[*]On the Datacenter's server, configure iptables (MASQUERADING ?) in order to route all traffic coming from the VPNs connections to Internet
[/list]

The theory seems to be good, but I don't have enough Linux expertise to achieve this, does anyone have already set-up something like this ?
Any idea/tutorial would be appreciated.

Right now, I'm stuck with [**vtun**]("http://vtun.sourceforge.net/") and creating a VPN for each iface. I can create 3 VPN easily (tap0, tap1, tap2), but I can't figure out how to force tap0 to use eth0, tap1 to use eth1, and tap2 to use eth2. Because, all 3 tunnels passes through the default route on eth1 (ISP1), instead of allocating 1 tunnel to 1 iface (ISP).

[SIZE="1"]**_References :_**
[LIST=1]
[*][ADSL Bonding &#8211; Howto and Review]("http://www.automatedhome.co.uk/Internet/ADSL-Bonding-How-To-and-Review.html")
[*][Multiple Connections to the Internet]("http://linux-ip.net/html/adv-multi-internet.html")
[*][Routing for multiple uplinks/providers]("http://lartc.org/howto/lartc.rpdb.multiple-links.html")
[*][Somebody with a similar problem on a mailing-list, but no answer]("http://unix.derkeiler.com/Newsgroups/comp.unix.bsd.freebsd.misc/2005-12/msg00619.html")
[/LIST][/SIZE]

---

### Post by tamird on 2009-09-12
BUMP!

I've spent upwards of 10 hours trying to get an answer to this exact problem. Apparently people on the internet think aggregation = LOAD BALANCE LOLOLOL.

Somebody help.

---

### Post by jward3010 on 2009-09-12
> **tamird said:**
> BUMP!

I've spent upwards of 10 hours trying to get an answer to this exact problem. Apparently people on the internet think aggregation = LOAD BALANCE LOLOLOL.

Somebody help.
No, people think what you're trying to do is COMPLICATED, sounds brilliant but poor Ubuntu users wouldn't necessarily know (I speak for myself of course only). Have you tried other networking forums?

Sorry for not much help but let us know how you're getting on, sounds interesting. Lucky is the person that has a 60Mbps (eventually) internet connection.

---

### Post by fwre01 on 2009-09-16
Hi Ellixis, Having had a quick look at this, the biggest problem i can see is IP space from different ISP's. Aggregating those 3 VPNs into some bond0 interface will necessitate the use of a public address from one of your ISP's - of which access into that one ISP cloud is then rate limited - I assume they are all different providers?

---

### Post by dvirdc on 2009-11-10
hey
have you found a solution ?
i wanna do the same here :)

---

### Post by ehybrid on 2009-12-07
It's easy enough to have multiple default routes, one needs to use iproute2 to set up multiple routing tables.   The linux advanced routing howto documents it reasonably, but can be tricky if you don't have a good understanding of TCP/IP.

I can assist further on a paid basis if you want to head down that path (email me or reply here)

Regards,
Ben.

---

### Post by mrgoll on 2009-12-18
Once more, I come back do drop off a quick update - and brevity increases with each response ;-0.

German Thread mentioning a howto which prescribes in detail a 2.6 vtun bonding solution (he uses 6 dsl lines) :

[http://forum.golem.de/read.php?16040,865522,1581227](http://forum.golem.de/read.php?16040,865522,1581227)

Actual step-by-step tutorial in German :

[http://www.rsm-connect.net/downloads/tutorials/vtun_and_bonding/tutorial.html](http://www.rsm-connect.net/downloads/tutorials/vtun_and_bonding/tutorial.html)

Google Translated to US English :

[http://tinyurl.com/VTunBondFromGerman](http://tinyurl.com/VTunBondFromGerman)

Enjoy. As requested earlier - please post feedback after having a pop (I will so the same when I have time).

---

### Post by logicstorm on 2010-02-20
Howdy all,
    I've been looking into this and similar problems for a while.  To be clear I want to restate what the "this" is:

1) Multiple low cost ISPs providing access to a single facility
2) The ISPs come with their own network address space and don't interoperate directly.
3) None of the ISPs will support BGP.
4) I want to aggregate all of the bandwidth
5) I want to perform transparent failover when possible if any of the ISPs stop routing for some reason.

Here's what I found:
   The best open source treatment of the problem I had seen was actually done with freeBSD 4.x.  Nothing says you couldn't use similar software on Ubuntu to duplicate the results.  Take a look:

[http://www.michaelbrumm.com/how-to-aggregate-bandwidth.html](http://www.michaelbrumm.com/how-to-aggregate-bandwidth.html)

   This was the most comprehensive solution for the open source community I could find.  I did find a lot of "Hey check out my hack!" stuff that was half fast treatment of this very complex problem.

   I also found several hardware, proprietary, solutions for dealing with this problem.  This is useful for a couple of reasons:
1)  It tells me there's a market for this
2)  It gives me an understanding of how they are treating the problem so that parallel solutions can be sought in the linux world.
3)  It lets me know the ceiling of money (read effort) involved in addressing the challange.  (IE:  if I was only willing to spend X $ I wouldn't have to spend Y hours).  Anyway, take a look at these:

The most promising one is this: [http://www.internetloadbalancers.com/](http://www.internetloadbalancers.com/)
    Click on network load balancing on the left.
Barracuda had a similar but seemingly less capable product.

[http://www.barracudanetworks.com/ns/products/link_overview.php](http://www.barracudanetworks.com/ns/products/link_overview.php)


Just my research so far- LS

Tags: bandwidth aggregation, multiple ISPs, linux, aggregate bandwidth, no BGP

---

### Post by aussie_ on 2010-05-03
There is a product that will BOND multiple ISP's and it dosn't require any co-opperation from the ISP's. It can do it with the same ISP or different ISP's.
:arrow: [www.frdmnetworks.com]("http://www.frdmnetworks.com") is the site. I spoke to a guy there called Jared and he was full of information and had a great knowledge of the ability to bond and how it compared to a load balancer. I had a great discussion with him about this.:popcorn:
 
I would sugest contacting them. 
 
They are internationaly around the globe.:KS

---

### Post by ieee754 on 2010-05-18
hey ppl. i just stumbled across your discussion. 

i have achieved this with vtun bonded vpn's using the opensource appliance zeroshell. 

i have detailed my approach in a howto here:

[www.ieee754.org]("http://www.ieee754.org")

naturally its point to point - but it address' the OP's needs if i have understood correctly.

i have over 10 links aggregated using this technique. for optimal performance all links need to exhibit similar latency and contention - otherwise, in my experience, a significant and adverse affect is imposed on performance.  

regards

ieee754

---

### Post by Replica2009 on 2011-05-03
Indeed it is possible to bond ISP connections without requiring any equipment on the ISP side \\:D/

The trick is to use a broadband bonding router. I heard of frdmnetworks.com, another one is mushroomnetworks.com - from their websites it sounds like they implement bonding at a higher layer than Phy or Mac and therefore no need for the ISP =D>

---

