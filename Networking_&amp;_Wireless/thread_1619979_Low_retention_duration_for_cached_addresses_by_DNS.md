---
title: "Low retention duration for cached addresses by DNSMASQ"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by michaelmestre on 2010-11-12
Dear all,

I am experiencing severe DNS delays today, so I tried to install DNSMASQ by following the instructions given on several pages on the web to make it function as a local DNS cache.

The installation was successful, and after editing the configuration files as instructed, I now have a working DNS cache on my computer.

However, it seems that the addresses are not cached for a long time ; for a given domain, the speedup lasts for a few minutes. If I try to access a previously visited domain once more after several minutes, a new (slow) external lookup is made.

Since websites' IP addresses are not changed every five minutes, would there be a way to tell **DNSMASQ** to **keep the IPs in the cache for a long time** (several hours at least) ?
This is very important for me because the DNS lag that I am experiencing makes external lookups last 10 to 20 seconds.
Thank you !

---

### Post by capscrew on 2010-11-12
> **michaelmestre said:**
> Dear all,

I am experiencing severe DNS delays today, so I tried to install DNSMASQ by following the instructions given on several pages on the web to make it function as a local DNS cache.

The installation was successful, and after editing the configuration files as instructed, I now have a working DNS cache on my computer.

However, it seems that the addresses are not cached for a long time ; for a given domain, the speedup lasts for a few minutes. If I try to access a previously visited domain once more after several minutes, a new (slow) external lookup is made.

Since websites' IP addresses are not changed every five minutes, would there be a way to tell **DNSMASQ** to **keep the IPs in the cache for a long time** (several hours at least) ?
This is very important for me because the DNS lag that I am experiencing makes external lookups last 10 to 20 seconds.
Thank you !
I believe you will find this is not a TTL (Time To Live) problem, but a cache size problem.  The TTL for a DNS entry is set by the SOA (the Source Of Authority), not the local cache. Since the default cache only holds 150 entries, it may be dropping older ones that you might want.  You can easily increase the amount of entries.  See [**_here_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html") for information.  look for the information on:```
-c, --cache-size=<cachesize>
```This sets the max amount of entries in the local cache.

---

