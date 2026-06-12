---
title: "duplicate routes"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2009-12-14
Considering this scenario:
I have 2 different connections to the internet on a single PC.
I have configured routing so that all the internet destinations are equally (same metric) accessible through both connections.

What happens?
-Does the kernel distribut connections on both routes equally?
-Does the kernel get confused and doesnot send packets at all?
-Does the connections become garbled (half the data sent through one and the rest through other route, thereby causing data corruption?
-Does the kernel use just one route and ignore the other?

---

### Post by lloyd_b on 2009-12-14
> **hammad1337 said:**
> Considering this scenario:
I have 2 different connections to the internet on a single PC.
I have configured routing so that all the internet destinations are equally (same metric) accessible through both connections.

What happens?
-Does the kernel distribut connections on both routes equally?
-Does the kernel get confused and doesnot send packets at all?
-Does the connections become garbled (half the data sent through one and the rest through other route, thereby causing data corruption?
-Does the kernel use just one route and ignore the other?

You can test for yourself via a 'traceroute', but I believe that the kernel will use only the first default route in the routing table if two are defined.

It *is* possible to "bond" the two interfaces, so that the workload is shared between them.  I'd suggest searching the forums or Googling for "bonding" for more information (don't bother asking me - I know it can be done, but not how to do it :) ).

I wouldn't worry about data corruption - TCP is *designed* to have packets traveling on multiple pathways without corruption.

Lloyd B.

---

