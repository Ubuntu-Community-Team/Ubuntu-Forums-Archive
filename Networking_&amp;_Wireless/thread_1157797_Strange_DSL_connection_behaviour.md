---
title: "Strange DSL connection behaviour"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by larry007 on 2009-05-13
I helped a friend upgrade to Jaunty the past week.  He has a dsl internet router (iBurst) which worked 100% with 8.10.  The connection through the network manager is really straight forward, connection takes a few moments as expected, and all seems heppy...  until trying to surf facebook or gmail, or retrieving email in Evolution.  

I double checked for all the normal gremmlins - DNS, gateway and all seems fine.  Fortunately I had my mobile phone to verify system settings, and upon connecting (via MTN), all of the above worked fine.  Thus I can eliminate system setup issues.

Thus the question remains, is it an ISP or Ubuntu network manager configuration issue?

---

### Post by superprash2003 on 2009-05-13
post output of **ifconfig** from the terminal . possible things you could try
1)disable ipv6
2)use opendns
3)change MTU

---

### Post by kryptikos on 2009-05-13
Is the router doing the DNS resolution or is it passing down the values from the ISP? 
From what you said the box is getting an IP address. Is it able to ping the router and past the router (say 4.2.2.2 a public dns)? 

What does ifconfig show with reference to stats? Are there excessive collisions, runts, giants, or carrier hits?

---

