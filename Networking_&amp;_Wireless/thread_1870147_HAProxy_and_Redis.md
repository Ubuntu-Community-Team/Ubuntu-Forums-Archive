---
title: "HAProxy and Redis"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by mikaelcrocker on 2011-10-26
G'Day!

So, I'm looking to setup HAProxy to monitor a redis server.  there are going to be 2 servers, but one is going to a failover.

How can I (using HAProxy) just send info to, lets say Redis00, then upon Redis00 going down, fail over to Redis01.

I looked at the readme online and saw the different loadbalancing methods (i.e. RoundRobin leastconn) and didn't see it.  I'm sure it's a matter of just managing front and back end stuff, but I'm stuck!

Any help would be awesome

Thanks mates!

---

