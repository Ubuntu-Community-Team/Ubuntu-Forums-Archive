---
title: "Internet is slower on linux than windows : Firefox lookups are slow DNS problems"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by cworth on 2009-10-08
I am posting this because it took quite a bit of searching to find the answer to my problem.  I noticed that the internet worked much faster on windows than on linux on the same (dual-boot) machine.  In Firefox, the site lookup times were long (as measured by the amount of time firefox reported Looking up sight xxx at the bottom of the browser). After going to a site once, though, the next lookup was almost instant (until quiting and restarting firefox)

After fiddling with DNS settings for a while, I found out about the program "dig" which directly queries DNS servers.  Dig was lightning fast, so DNS lookups weren't the real problem.  

What was the problem was that ipv6 support was turned on in Firefox.  After typing about:config in url bar, searching for ipv6, and disabling ipv6, the lookups times disappeared, and the performance was comparable (if not equal or better than) my windows machine.

Just wanted to add this to the fix it solutions out there for this problem.

---

