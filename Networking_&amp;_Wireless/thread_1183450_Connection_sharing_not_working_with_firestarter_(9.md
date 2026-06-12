---
title: "Connection sharing not working with firestarter (9.04)"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by pape on 2009-06-10
I have a fresh Ubuntu 9.04 install, eth0 and eth1 are configured and working (pings ok etc). 

eth0 is for internet and eth1 for local network.

I've set firestarter to share the connection, but it's not letting traffic through (local machines can ping the sharing machine but can't get to internet).

I've done this a dozen of times before with different distros, so either I've forgotten something elementary, or Ubuntu 9.04 by default blocks the traffic. Any insights appreciated.

[EDIT] 
Human error - my local machine had gateway wrongly configured.

---

### Post by oygle on 2009-06-10
Your syslog will show what is being blocked, if anything is being blocked. I use Firestarter with Intrepid, and connection sharing works okay.

---

