---
title: "How to allow listen on two different NICs"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by mr.josep on 2009-07-27
Hi:
My system is an apache server connected to 2 different subnets using 2 NICs card.
Apache is Listening on 2 address: one for every subnet
I need to serve http pages for both subnets.
-----
Problem:
Using 'route' command, I can configure 1 'default' interface.
The system is able to serve only the request that comes from the 'default' interface.
The requests that comes from the other NIC, ends with timeout on the client.
-----
Question:
Are they a way to configure the system in order serve request for both NICs/subnets?

Thanks in advance

---

