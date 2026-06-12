---
title: "Linksys router, DNS issues but only with my routero"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by markdjones82 on 2009-03-19
All,
  I cannot figure out what the problem is here. I can connect to other networks and i can get out just fine.

What happens with mine is I get connected and I can load one page, then it just hangs or runs very slow when trying to connect to a new page.  I have tried using different DNS servers but still have the same problem.  My windows servers works just fine.  
I am running a wireless linksys GS. Are there any known issues with this router?

I ran a wireshark scan and I get a:
who has 192.168.1.102 tell 192.168.1.1 till it times out.  Anyone where I can start?

---

### Post by markdjones82 on 2009-03-20
Ok, I found the issue.  I have vmware server installed and NAT. NAT was setup to use my routers address and therefore causing a conflict.

---

