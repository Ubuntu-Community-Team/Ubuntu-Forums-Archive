---
title: "Apache2,MYSQL,Config failover"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by infecticide on 2009-03-09
I have a server at home hosting a few web pages. I want to setup fail over capability.

I have the space and the equipment to provide a fail over site across town.  But I don't have the knowledge :)

Components
----------
- Apache2
- MySQL
- Server configuration

How do I go about configuring the systems so that:
--------------------------------------------------
- If the primary goes down the secondary takes over and returns back to the primary once it returns
- While the secondary is running everything is read-only so reverse replication won't be necessary, or a reliable way to reverse replicate.

I'm certain that reliable reverse replication with MySQL is probably easy to accomplish and I already use RSYNC to backup configuration and web data to a NAS.

I am hosting my domain name through Yahoo! and something that seems promising is setting up the primary and secondary name servers to my primary and secondary servers.

Any thoughts?

---

