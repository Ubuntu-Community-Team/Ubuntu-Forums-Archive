---
title: "squid cache to reduce wireless modem usage"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by astrand on 2010-11-20
Hi All,
I live in a rural area and all of our internet traffic courses through a wireless modem with a 5gig/month limit.  The modem is plugged in to a cradlepoint router which serves up wifi as well as connecting our wired machines.

I was wondering how it might be possible to set up a squid proxy cache to reduce the amount of data that is repeatedly downloaded when browsing.  

I have a inkling of how this might work if one of the wired machines served as a gateway, but is it possible with a router/modem combo serving a gateway?

Thanks 
 Allan

---

### Post by SeijiSensei on 2010-11-20
Take a look at [Dan's Guardian]("http://dansguardian.org/") and see how it is setup.  If you can put the squid box between the router and the internal network, that's the easiest thing, but I believe DG configures squid to work on an outboard server as well.

That said, don't expect miracles from Squid.  First, your browsers will already be caching a lot of commonly used items.  Just as a test, I looked at the number of HITs and MISSes in the logs from a Squid cache I manage for a medium-sized organization.  In ten days, there were about 1.4 million misses and 190,000 hits.

---

### Post by lunix- on 2010-11-20
If wireless to wireless is needed, I would use a old computer with debian + two wireless cards connected. 

If not, same procedure but without wireless acting as AP and cabled net instead..

You connect to net with one, and configure the other one to act as AP. 
(WPA2 (AES), Dont use WEP as you wouldnt want people stealing your precious gigas)

Install and configure squid and your good to go. (almost plug and play)

**Not sure if it would be worth the hassle though**, squid would probably not help very much in a small network..  but sure its possible. And could be a very good learning experience :)

Bonus: That old computer could do a lot of other useful stuff too.. Music server (MPD), Samba+NFS fileserver, CUPS or whatever..

---

### Post by astrand on 2010-11-21
Thanks,
I thought that it might not help a lot, but at the prices that wireless corps charge for >5gb usage, a little bit of bandwidth caching might add up to real money.

As for a dedicated gateway, I agree it could do a lot of things, but I already have too many boxes (several myth boxes) to maintain and pay the the power bill for 

a.

---

### Post by eentonig on 2010-11-21
Your squid doesn't have to be inline. You can just install squid on a PC/server besides the other clients and have them configured to use a proxy for the network traffic.

If you want to enforce the proxy usage, just block all internet access from your LAN, except for the squid IP address.

---

