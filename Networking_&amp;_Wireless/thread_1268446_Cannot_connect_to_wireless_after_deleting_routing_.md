---
title: "Cannot connect to wireless after deleting routing rules"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by nawar on 2009-09-16
Hi!

Yesterday I was playing with my routing table with route command. I deleted all the rules in the table including link-local and I was trying to recreate them manually (I was connected to my wireless at that time). 

After adding the same rules which I deleted from the routing table. I wasn't able to communicate to my access point. I rebooted my box thinking this shall be fixed with a clean boot, but I ended up with empty routing table. 

Since that I was trying to connect with my access point but with no success, as it gets authenticated and associated with the APN but cannot precedes with the whole process.

Sorry for not attaching syslog file as it was cleared and couldn't find a trace to that (I have different problem now). I have no clue of this is related to avahi, but I hope someone has encountered such problem. 


Solved:
I purged my avahi-autoipd package and reinstalled again. Everything returned back to normal.

Thanks for help

---

