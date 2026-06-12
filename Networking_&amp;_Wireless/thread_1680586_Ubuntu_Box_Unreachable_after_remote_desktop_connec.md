---
title: "Ubuntu Box Unreachable after remote desktop connection"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by rjaus on 2011-02-02
I've got a strange issue connecting to my ubuntu box which seems to be caused by launching a remote desktop connection.

I have two PC's connected over ethernet via my home modem/router.

PC 1 runs windows 7 and an xampp stack and is my php application server.  It connects to a number of java applications running on my 2nd PC.

PC 2 runs ubuntu desktop 10.10 and launches java programs on ports 4444 - 4454.

Everything runs fine normally.

But if I use UltraVNC to remote desktop into the Ubuntu PC (from PC1 windows 7) and load up the java applications from a terminal PC1(windows 7) can no longer connect to the java applications running on ports 4444-4454.  

If I launch the java applications from the terminal before I remote desktop in with UltraVNC everything works fine...

I'm confused as to why this occurs only in this circumstance.

Any ideas where to start looking to resolve the issue?

Thank you,

P.S Loving the new ubuntu, have used it in the past, but never been so impressed with it.

---

### Post by rjaus on 2011-02-02
same thing occurs if I SSH into the box with Putty from PC1.

---

