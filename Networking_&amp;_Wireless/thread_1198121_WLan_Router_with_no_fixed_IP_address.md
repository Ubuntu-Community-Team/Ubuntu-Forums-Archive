---
title: "WLan Router with no fixed IP address"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by Yumi on 2009-06-27
We have a shared network over a couple of offices. One router 192.168.1.1 is the default gateway to the internet. In every office we have Wireless (Sub) routers set to receive their IP from the DNS server (hope this description is right).

I want to change the WEP key on my office W-Lan router, but the default IP address does obviously not work. How can I find out the current IP address? Am connected to my router by wire and Wireless.

---

### Post by jimv on 2009-06-27
Open a terminal and type "route -n".  The IP address in the Gateway column is your router.

---

### Post by Yumi on 2009-06-27
Thanks for the tip. But it comes up with 192.168.1.1 the default gateway. A list with all the active IP's would be useful. Now over the weekend only the routers and server are on.

---

