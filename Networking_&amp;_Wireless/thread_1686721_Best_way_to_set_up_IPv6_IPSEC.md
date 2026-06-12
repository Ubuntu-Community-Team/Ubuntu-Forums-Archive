---
title: "Best way to set up IPv6 IPSEC?"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by SoftwareExplorer on 2011-02-12
I've been using IPv6 on my local network and through a Hurricane Electric IPv6 tunnel. 
I've heard that one of the built in features of IPv6 is encryption, both scrambling the data and authenticating where the traffic came from. 
I've done some searching and heard of SWAN and Racoon, but some of the stuff I found is old and I would like to know what the easiest/best way to set up IPSEC for IPv6 is.

---

### Post by movieman on 2011-02-12
Wish I knew; as I said in the other IPV6 thread, I've never managed to get IPSEC to work with IPV6, whereas it works fine with IPV4.

---

### Post by lemming465 on 2011-02-13
I haven't tried v6 IPSEC yet myself, either.  Support can be just missing, e.g. Cisco routers might do it, but until 2010 and firmware 8.3 their ASA corporate firewall appliances wouldn't even try.  Definitely expect to find interoperability issues if you are going between heterogeneous equipment.

---

### Post by SoftwareExplorer on 2011-02-15
I got ESP set up manually using setkey. So I guess my problem is more of knowing how to set up racoon. 
As far as various OS's, I'm running two Ubuntu computers at home, so I shouldn't have trouble if Ubuntu supports IPv6 IPsec.

---

