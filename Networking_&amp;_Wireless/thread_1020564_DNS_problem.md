---
title: "DNS problem"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Turnip on 2008-12-24
I seem to have a problem with very slow DNS lookups, as evidenced by the following:

```
$ time ping -c 1 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=243 time=112 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 112.772/112.772/112.772/0.000 ms

real	0m10.164s
user	0m0.004s
sys	0m0.000s
$ time ping -c 1 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=243 time=108 ms

--- 74.125.45.100 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 108.115/108.115/108.115/0.000 ms

real	0m0.112s
user	0m0.000s
sys	0m0.000s
```

I thought this was a problem with my ISP, but I have now come to my parents' house and still have the problem, so it seems to be my computer. It occurs whether connected via a wireless or wired connection.

I really have no clue what to do about this; I am fairly competent with linux but don't have a great deal of networking knowledge. If anyone has suggestions I would really appreciate it.

Thanks, happy christmas :)

Jon

---

### Post by roelpeeters on 2008-12-24
This is not a problem of DNS lookups. What you are looking at are Ping times which tells you how much time it takes for a packet to reach the host you ask it to contact (true, based on a name it needs to do a DNS lookup).  A difference of 4 ms on values like 108 and 112 is minimal and not to worry about. You cannot conclude that DNS lookup costs 4 ms for several reasons: first, DNS is usually cached, at several levels (meaning on next pings, the DNS lookup is the time only for searching in the cache). Second, you have very little data to compare. 
I am not sure what your problem is, on my system (via wireless through ADSL) I have a ping time of 143ms to google, and the rest of the networking speed is normal. If you are worried about DNS lookups try to use **nslookup**. You will see that the DNS lookup is very fast. Speed problems with networking my depend on a lot of things. How do you tell the internet connection is slow? Browsing? Watching YouTube?

Marry Christmas!

---

