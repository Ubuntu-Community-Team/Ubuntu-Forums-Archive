---
title: "DNS query: dig disagrees with .... dig"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by hartz on 2012-05-17
Hello.

Why would I get different results from the following two commands:

dig +trace +all gmail.hartz.co.za
   vs
dig +all gmail.hartz.co.za

The first returns the correct result - ghs.l.google.com

The second returns the stale wildcard from the DNS of my old hosting provider.

For what its worth, the above example is shortly after changing hosting provider and in the process of learning about DNS and web hosting in general.  The DNS update is still probably not fully propagated through all DNS servers.

For what it's worth, nslookup, ping, getent hosts, and friends return the same result as do dig without trace.

I'm guessing that this will resulve itself over the next 24 hours...?  But why would the +trace flag on the dig command affect the actual result?

Thanx.

---

### Post by hartz on 2012-05-17
OK, according to the manual dig operates differently when tracing is enabled compared to when not, specifically, I quote:

```
       +[no]trace
           Toggle tracing of the delegation path from the root name servers for the name being looked up.
           Tracing is disabled by default. When tracing is enabled, dig makes iterative queries to
           resolve the name being looked up. It will follow referrals from the root servers, showing the
           answer from each server that was used to resolve the lookup.
```

So I just have to wait for DNS propagation to complete. :-)

---

