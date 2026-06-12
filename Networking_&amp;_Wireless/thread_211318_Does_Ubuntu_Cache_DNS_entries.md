---
title: "Does Ubuntu Cache DNS entries"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by faddat on 2006-07-08
Hello, my ISP had some bad DNS entries for some websites that I like, so I changed DNS servers to those that a friend who can access the sites uses.  I still cannot access the sites and I am wondering if there is somehow a cache kept of of the bad DNS entries on my computer.  

Thanks for your help!

-Jake

P.S.

Can I clear my DNS cache, if Ubuntu does cache DNS entries?  If so, how do I go about doing this?  Thanks!

---

### Post by tturrisi on 2006-07-08
afaik Ubuntu does not cache dns entries unless running a dns server (bind).  Clients cache dns entries though.  Hosts can be cached via the /etc/hosts.xxx files.

Check your:
/etc/resolv.conf
for your dns servers list.

also, delete the browser cache.

also, Firefox retains a dns cache.  Type **about:config** in the FF address bar and alter these items: (turn off & back on later)
```
network.dnsCacheEntries [Integer] - This setting determines how many entries should be held in the Firefox DNS (Domain Name System) cache. Whenever you enter a web address in Firefox, it needs to convert that text address into an IP number. It does this by looking up the name and IP number through a DNS server. By holding DNS entries in a local cache, the next time you want to go to the same site Firefox can load it up much faster. By default Firefox holds 20 entries in the cache. I recommend changing this number to match the number of sites you regularly browse each day. More importantly, check the setting below to ensure DNS entries are kept up to date.

network.dnsCacheExpiration [Integer] - This setting determines how long the cached DNS entries (as set by the network.dnsCacheEntries setting) are held before they are discarded. The default is 60 (seconds), however before changing this setting consider the pros and cons - the longer cached entries are held, the quicker your browsing may be, but the longer it may take for Firefox to be aware that a site which was temporarily considered unavailable (unresolved) is now accessible (resolved).
```

---

