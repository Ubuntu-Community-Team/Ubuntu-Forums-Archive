---
title: "Optimizing Ubuntu for Low Quality DSL?"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by matthanielcm on 2011-04-28
I have a friend who is using Ubuntu 10.10 Netbook Edition on their netbook and well they love it. However, I notice that at times (if not all the time) their internet is ridiculously slow. Yes, it's a 1 Mbps download connection, but I still think it's a little slow and at times I can't even get it to load a website. I'm thinking if I adjusted the MTU within Ubuntu, it might improve, if even only slightly. I believe the router is set to 1490 or 1500, I haven't really looked yet. Any ideas on how to do this, or if it's even worth my time?

---

### Post by sanderj on 2011-04-28
> **matthanielcm said:**
> I have a friend who is using Ubuntu 10.10 Netbook Edition on their netbook and well they love it. However, I notice that at times (if not all the time) their internet is ridiculously slow. Yes, it's a 1 Mbps download connection, but I still think it's a little slow and at times I can't even get it to load a website. I'm thinking if I adjusted the MTU within Ubuntu, it might improve, if even only slightly. I believe the router is set to 1490 or 1500, I haven't really looked yet. Any ideas on how to do this, or if it's even worth my time?

1 Mbps should not result in slow connections. My thoughts:

- what are the specs of the machine running Ubuntu: CPU and Memory.
- have you checked the speed via [http://speedtest.net/](http://speedtest.net/)
- do you use wifi? If so, what's the speed if you use a wire?
- it might be a slow / non-responsive dns. Put "8.8.8.8" as the first nameserver in /etc/resolv.conf to see if that helps.
- I would *not* play with the MTU

---

### Post by matthanielcm on 2011-04-30
I had another look at the router and it actually looks like it's supposed to only get 786 Kbps Down. I did a speedtest.net test on both wifi and wired connections and found negligible speed difference. The results were 0.65 Mbps down and 0.25 Mpbs up for both connections. Changing the DNS didn't change the speed much. The specs of the computer are 1 GB RAM and 1.66 GHz dual core Atom processor. I always though the quality of the connection itself is quite bad, there might be some old wiring in this place. Any thoughts?

---

### Post by sanderj on 2011-05-01
> **matthanielcm said:**
> I had another look at the router and it actually looks like it's supposed to only get 786 Kbps Down. I did a speedtest.net test on both wifi and wired connections and found negligible speed difference. The results were 0.65 Mbps down and 0.25 Mpbs up for both connections. Changing the DNS didn't change the speed much. The specs of the computer are 1 GB RAM and 1.66 GHz dual core Atom processor. I always though the quality of the connection itself is quite bad, there might be some old wiring in this place. Any thoughts?

If speedtest tells you have 1 Mbps, how can the wiring be bad or the casue for slowness?

What do you get if you type "time host www.google.com"?

```
sander@netbook:~$ time host www.google.com
www.google.com has address 209.85.147.103
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.

real	0m0.295s
user	0m0.012s
sys	0m0.008s
sander@netbook:~$

```

---

