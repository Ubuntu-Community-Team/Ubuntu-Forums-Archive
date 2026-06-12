---
title: "Crashplan will not accept inbound backups"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by baz.g on 2013-08-13
Hi all,

I cannot seem to get Crashplan to accept inbound backups from my friends on both my Ubuntu 13.04 64bit machines. They are added correctly in Crashplan but it just constantly sits there saying "waiting for connection". This is exactly the same with 3 different friends (so 3 completely different IPs). I have tried looking for the problem on the Crashplan support pages but it just mentions restarting the service (done), or telnet'ing and forwarding the port.

I have added port 4242 as a port triggering port (because I have 2 machines needing the same port) but it has made no difference. If I try telnet'ing to any of the friends it says connected but I dont then get the unintelligible string like you are supposed to. I have my 2 machines backing up to each other internally within the LAN no problem (they telnet too), and 1 of the machines is also backing up to the Crashplan cloud.

I havent enabled any software firewall on either ubuntu machine.

I havent yet sent a support request to Crashplan because I thinking that it may be an issue with my ubuntu installations rather than Crashplan (because I am unable to telnet)

Can anybody help please?

---

### Post by baz.g on 2013-08-15
Solved! It turns it out it was an issue on Crashplan's side affecting everybody, they have now fixed the issue on their servers :)

---

