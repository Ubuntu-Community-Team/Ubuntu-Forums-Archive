---
title: "LTSP multi NIC server?"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by morphyrichards1 on 2013-06-12
I understand it's best to keep 15 LTSP clients per 1000mbps sub net. I am trying to provide a network for 30 users simultaneously.

Is it feasible to do this using one "standard" Edubuntu LTSP server with 3 NICS?
1 NIC for internet and 2 for each group of 15 users?

I've been looking for pertinent information but not finding much of use.

I imagine I would update the ltsp dhcpd.conf file but would appreciate some pointers before I start breaking my network.

Would it just be a case of defining two subnets in dhcpd.conf and configuring interfaces?

[COLOR=#333333][FONT=Ubuntu Mono]subnet 192.168.1.0 netmask 255.255.255.0 {
[/FONT][/COLOR]etc etc
[COLOR=#333333][FONT=Ubuntu Mono]subnet 192.168.2.0 netmask 255.255.255.0 {[/FONT][/COLOR]
etc etc
Also - is this idea even worthwhile in terms of making a less laggy user experience (I would rather avoid building a whole extra new server if I can)

Thanks

---

### Post by newbie-user on 2013-06-13
Sure, if you're planning to subnet your network that way. Just have the DHCP server point the users to the appropriate IP address and make sure your DHCP server is set to run on both NICs used for LTSP.

Subnetting is just one thing that will help reduce lag by reducing the amount of network traffic. I think it's more important to have a powerful server, since you're already running gigabit subnets.

---

### Post by morphyrichards1 on 2013-06-13
Thanks for this.

So, eth0 to switch to 15 terminals on one side of room and eth1 to 15 terminals on the other side.

I will give it a go.

In terms of servers, currently I'm running the LTSP server with a AMD Sempron 3Ghz processor with 8GB RAM. Its only a single core processor and I'm already noticing performance issues, even when running lightweight versions of X desktops.

I think I might change it up to AMD FX-6 Six Core 3.3 GHz Processor. This will involve getting a new motherboard as well, it's tricky as I have a tight budget and need to fit out 3 classrooms.

Which would be better, a quad core at 3.6 GHz or six core at 3.3 GHz? It would seem to me that as the server has many independent jobs (users) it would do it better over more processors running at a slightly lower speed.

---

### Post by newbie-user on 2013-06-16
I would go with more cores. I suspect that your users will not be doing anything that is really cpu intensive, so a slight speed advantage of 300MHz won't do much. More cores would be better to support more users. 

Have you considered looking into refurbished servers? I've gotten some dual quad-core xeon servers for $300 or less at geeks.com. I then get some server memory off of ebay at really low prices. At these prices, you might be able to double up on servers for redundancy or load balancing.

---

### Post by morphyrichards1 on 2013-06-19
Thanks for that. Am in the UK but will look into an equivalent supplier. Out of curiosity is something like this advertised reconditioned server

> Dell R710 server (1 x 4 Backplane) configured with 1 x E5630 Quad-Core 
(2.53Ghz 12M Cache, 5.86 GT/s QPI, 80W TDP, Turbo, HT), DDR3 1066Mhz 
processor, 4GB Ram

Better than
> Product Description    AMD Black Edition AMD FX 8120 / 3.1 GHz processor
Product Type    Processor
Processor Type    AMD FX 8120
Processor Socket    Socket AM3+
Clock Speed    3.1 GHz
Manufacturing Process    32 nm
Multi-Core Technology    8-core
Smart Cache Memory    L3 8 MB
64-bit Computing    Yes
[I]
and with with 8 Gigabytes of standard DDR3 SDRAM memory?[/I]


From just looking at the numbers the newer AMD basd system seems better to be (and assuming that these are applications servers only with minimal need to access their own hard disks. The actual file server is elsewhere using SCSI.

---

### Post by newbie-user on 2013-06-19
Certainly the AMD will be better if you're comparing those two. I was under the assumption that you didn't have a server to use yet and that you were going to build one. I recommend a reconditioned server for tight budgets. I think you'll need a lot more RAM, though.

---

### Post by morphyrichards1 on 2013-06-20
Thanks again :-)

---

