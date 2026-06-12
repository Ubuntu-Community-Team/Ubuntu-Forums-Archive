---
title: "Connection Records (Script?)"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by lordhaworth on 2009-05-27
Hi all,

Not sure if this should be here or in programming stuff. The wireless in our house seems to systematically die at roughly the same time every day (it may even be more than once per day). I was wondering if there are any scripts about that monitor changes in internet connection and write them to file i.e.
 
connectionStatus(connected/disconnected) |       time        |                 (count?)


the count would be useful for analysis (making it cumulative).

As I said this may need to be moved to programming stuff. I code myself, but not really anything like this so have no idea if its simple or what...

Cheers

Tom

---

### Post by puppywhacker on 2009-05-27
You can use MRTG to monitor your network connection. Every 5 minutes it would check the throughput of the network, log it and create a nice graph for you.

---

### Post by lordhaworth on 2009-05-27
Thats awesome, cheers ill look into it

---

