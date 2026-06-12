---
title: "Cable modem bonding"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by lobstah on 2011-05-23
I know load balancing is an inexpensive way to use multiple internet connections.. but what about bonding? Can I bond cable modems to aggregate the speed?

---

### Post by never say never on 2011-05-23
The short answer is NO you can't.

Depending on your cable company, cable box, and cable network you may be able to ask your provider to turn up the bandwidth and get more throughput through one modem.

The reason you can't bond them is that needs to be configured from the Head End (Cable Company side of the connection) as well as on your end.  Docsis 3 cable modems can bond the cable channels and do the heavy lifting, that is why they now have the 'turbo' speeds.

---

### Post by vunity on 2011-05-23
[COLOR=black][FONT=Verdana]Never say Never,[/FONT][/COLOR]
 

[COLOR=black][FONT=Verdana]You should never say no. lol. [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]We are [[COLOR=#284b78]vUnity[/COLOR]]("http://www.vunity.com/") and in Los Angeles we bond DSL circuits without ISP support. We use virtual tunnels to create a point to point links and then bond those links together logically. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Using four 10Mbps DSL lines we typically deliver [[COLOR=#284b78]40Mbps[/COLOR]]("http://vunity.com/plans/x4") of aggregated speed. We can work with cable modems like you asked and frequently combine DSL and cable to create a diverse path for VoIP and other mission critical applications. Even if we're not using separate technologies like your Cable modem's and adding DSL to form diverse paths, we can still deliver multiple DSL lines through multiple providers for high bandwidth and fault tolerance. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]It's true bonding and seems a little complicated on the backend.. we call it vUnity x4 and seamless to the end user.. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Let me know if I can answer any questions, :)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]-Brian[/FONT][/COLOR]

---

### Post by never say never on 2011-05-23
Ok, I didn't say it couldn't be done, just that an end user can't do it.  I stand by that.  

You have to have control over both ends of the connection (addressing).  You are accomplishing that, apparently by creating VPNs, between the end users equipment and yours and routing there traffic from your location.  I would expect that with VPN and the extra steps latency is higher than average, though redundancy and overall throughput are increased.

A lot of things are possible when you control both ends of a connection.

Further, I submit that unless he also wants failover / redundancy, it will be far cheaper to have the cable company increase the throughput than to have multiple accounts and pay your company to 'bond' them.

---

