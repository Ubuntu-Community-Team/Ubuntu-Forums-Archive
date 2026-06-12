---
title: "Connecting laptop to different networks not working cleanly"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by cnkbrown on 2006-06-20
Since update to Dapper, I notice that when I've had me laptop networked at home, and then bring it to work and connect there, networking acts 'funny'. some examples;

   Even though I receive a DHCP lease at work, I can't access work servers until I open a terminal and ***sudo dhclient eth0***, causing the lease to be dropped and then renewed.

    Many times, ntpdate does not seem to be run, even though it has a ***/etc/network/if-up.d/ntpdate*** in place.   Again, I have to open a terminal and ***sudo ntpdate*** manually.

    It's almost as if the network connection doesn't fully come up - which would explain why ntpdate doesn't run.

    It must be something odd about the work environment, since this type of thing doesn't happen when going from work to home.

    Any ideas about what I should look at to isolate the issue further?

---

### Post by Sgood1971 on 2006-06-20
This happens to me when I hibernate or suspend my laptop while connected to one network, then wake it up at another. It will get an ip in the right range, but until I cycle it, no connection. If I power down, no problem.

---

