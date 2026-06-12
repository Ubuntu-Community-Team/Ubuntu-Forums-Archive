---
title: "Host Ubuntu utilizing public connection of Guest Windows OS"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by bryan_r59 on 2010-08-18
I recently purchased an expensive Anonymity service  and would like to use the proxies for Ubuntu, but only my Windows Guest OS can run their program.

Their service is in fact working, but I would like to utilize the public connection it creates so that my host OS can also use the services. Mainly I am interested in getting the proxies to work for Ubuntu.

I have tried taking the IP address it gives me and using it. But the address refuses my connections. It may be a matter of finding the right port number. 

What I do know is their program creates a public network connection.  That connection is what I want Ubuntu to utilize.

I visited the support channels of virtualbox, and one guy had me set adapter 1 to a bridge and adapter 2 to a host only. This makes it so my host OS can use the connection of my guest, which is using eth0 wired connection. 

But it isn't what I want because I would still be using the eth0 connection without being anonymous.

So How can I ?:
1. Start my GUEST OS (windows) with the regular eth0 connection
2. Enable the Anonymity service so it generates the public connection
3. Then have my HOST (ubuntu) go through that public connection

---

