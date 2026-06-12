---
title: "Bind9 Reverse Zone not Transfering"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by dusfer on 2012-10-21
Hey Guys,

So I have had a setup of Bind9 working for about two weeks ago. Today when I added a record (updated serial on both forward and reverse zone) the slave server did not load most current reverse zone record. When I restart the slave server, and then look in /var/logs/syslog I get no errors. Any ideas why this might be happening? I am running Ubuntu 12.04 on both servers.

Thanks

--Update--

If i delete the zone manually from the slave, it will successfully transfer the newest zone file from master. But any changes after that will revert back to the same issue. So basically to get the slave to transfer reverse zone from master, I must delete the slaves zone file.. any ideas?

Thanks!

---

### Post by Budewiser on 2012-11-30
Any resolution to your issue?  I'm having the same problem.

Thanks

---

