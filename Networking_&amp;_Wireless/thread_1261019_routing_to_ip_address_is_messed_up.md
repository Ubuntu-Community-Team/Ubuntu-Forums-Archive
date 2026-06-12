---
title: "routing to ip address is messed up"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by vfclists on 2009-09-08
the routing to a single IP address on my system is messed up. I believe that it is linked with some stale routing data in some cache some where. DNS resolution works fine, it just seems that connection to port 8080 doesnt.

I have tried restarting the network and rebooting the server but it makes no difference.

pinging works, windows works. Another Ubuntu system I configured is not working. They are both based on coLinux and I wonder if that has something to do with it.

It seems so illogical to me.

Is there some command to fix that.

---

### Post by Bucky Ball on 2009-09-08
System->Admin->Network. Go to the DNS tab. You should have the IPs of your DNS servers in there. If you are running a static IP on the local machine, make sure your router is not serving it one as there will be a clash.

For your connection, make sure you have the correct DNS and gateway and make sure port 8080 is forwarded through the router (but if Windows is working on this port it should be).

---

