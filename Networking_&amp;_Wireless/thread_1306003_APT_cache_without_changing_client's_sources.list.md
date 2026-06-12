---
title: "APT cache without changing client's sources.list"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by mightyiam on 2009-10-30
Dear & supportive community,

While there are solutions to APT network caching like apt-cacher and approx, I'm looking for some way to have a local APT cache that local clients will use without having their sources.list changed to point to the local APT server. This will be nice for me and perhaps for others as well.

In my case, the APT cache server is also the machine through which the APT clients get Internet. This is done by NAT. So I'm thinking that maybe there's some way to divert all the APT HTTP requests to the local cache instead of where they would normally go. Perhaps this solution doesn't even need a local APT repository but just an HTTP cache server to cache the APT mirrors. Any idea on this, please?

Blessings.

---

### Post by i.r.id10t on 2009-10-30
You could set up a local apt mirror and then either use iptables to redirect connections to the apt server or play with DNS and get the names to point to your local IP instead of ubuntu's or whoevers.  Or just set up a squid proxy, but that will only help if people download around the same time as eachother.

Of course, if you set up your own apt mirror and set your client machines to use it, you could just make it publicly available as well.... no dns or iptables trickery needed.

---

