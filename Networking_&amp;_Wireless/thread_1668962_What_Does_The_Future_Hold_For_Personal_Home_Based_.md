---
title: "What Does The Future Hold For Personal Home Based Web Servers When IPv6 Rolls Out?"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by garryconn on 2011-01-17
For the few thousands of people who have a little too much time on their hands who create personal web servers and host them using their local ISP on  dynamic IP addressees.... what does the future hold for me.. {COUGH} ... I mean, **them** when IPv6 rolls out?

---

### Post by lemming465 on 2011-01-17
In the long run, hosting on IPv6.  Ideally, dual-stack hosting on IPv4 plus IPv6 during the transition period.  In the short run, confusion, pain, and details that vary depending on how your ISP is handling things.  Plan on having to upgrade your WIFI and broadband gear; the v6 transition is going to be lot like converting from analog TV to digital.

The rough timeline for IPv4 depletion and IPv6 ascendence might be:
IANA runs out of /8's globally around February 2011.  Multiple of the 5 RIR's run out late in 2011, definitely including APNIC.  ISP's start running out in 2012.  Very little new IPv4 available in 2013 and beyond.  Widespead world-wide IPv6 probably arrives too late, around 2015, so let's call 2013 the "IPocalypse" :-(  IPv6 being the dominant (99% of traffic) internet protocol maybe in 2017. Tier-1 ISP's turn off IPv4 backbone internet routing, maybe 2020.  (Router load for v6-only is about 1/18th the load for dual-stack IPv4 + IPv6, so they have a very strong incentive to collude to make that happen).  Last IPv4 device decommissioned maybe 2036.

Early adopters don't have to wait for their ISP's; they can upgrade their wifi routers to something that passes IPv4 protocol 41 (IP in IP), sign up with a tunnel broker like gogo6, sixxs, or hurricane electric ("www.tunnelbroker.net") and get a a routed IPv6 /64 or even /48 as a "6in4" point to point tunnel link today. They need a DNS provider that can handle IPv6. The tunneled v6 latency will suck compared to native, but it will mostly work.

ISPs in the US will likely roll out "6rd" v6 before they get to native, where if you upgrade your broadband modem (cable or dsl), it sets up a IPv6 over IPv4 protocol 41 tunnel to a relay at the ISP.  This will be decent v6; you get a native address, only a 20 byte penalty on MTU, and only add ~3 hops of latency.

There are other tunnel protocols, but 6to4 (v6 addresses starting with 2002::/16) requires a public v4 address as well as protocol 41 support, so most home users can't use that.  Teredo (v6 over UDP) can be used from home, but only by masochists.  On Linux install the "miredo" package if you want to play with Teredo; expect hideous latencies and about 15% unreachable sites.

An interesting unresolved question is how much dual-stack "heavy" (native v4 + native v6) there will be.  This is how corporations should do their public-facing services such as web sites.  In the US federal agencies are mandated by OMB to do this by September 2012.  If you use a hosting provider, this is what you want to insist on them supporting.  

However, new customers may be on public native v6 and going through some kind of carrier shared NAT gateway to get to legacy v4 stuff.  In the US, this is already starting to happen with the 4G smartphone rollouts; e.g. Verizon's LTE network that went live in December is native v6, not native v4.  Here we're talking either "NAT64" (v6 only, translated by carrier to v4), or NAT464 (native v6, tunnel private v4 over v6 transport to carrier NAT44 device).

Keep an eye on the emerging "port control protocol", as that is what will be needed to allow inbound connections through carrier NAT devices. Maybe.

Bottom line: for inbound web services, your two best bets are 6in4 point to point tunnels now and native v6 later.

---

