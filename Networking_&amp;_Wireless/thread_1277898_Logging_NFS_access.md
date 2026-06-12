---
title: "Logging NFS access?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by negativ on 2009-09-28
I am trying to find a relatively automated way to collect statistical information about usage patterns of my NFS exports.

For example, let's say I am exporting

/exports/group1 

which includes 

/exports/group1/alpha
/exports/group1/bravo
/exports/group1/charlie
/exports/group1/delta
/exports/group1/echo

and 

/exports/group2

which also includes a subdirectory structure similar to the above.

I am pretty sure that (for example), files in /exports/group1/bravo and /exports/group2/delta are being accessed almost constantly, while things in /exports/group1/echo and /exports/group2/alpha might only be accessed once a month.

I would like for the server to collect this information and log it for me.  I would like to be able to assess usage patterns over time.  I'm reasonably sure this is doable, but I don't know where to start.  

Helpful hints appreciated. :D

---

