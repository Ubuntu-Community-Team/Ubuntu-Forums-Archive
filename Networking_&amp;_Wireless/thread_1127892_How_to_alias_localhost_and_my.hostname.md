---
title: "How to alias localhost and my.hostname"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by odror on 2009-04-17
My computer have 3 hostname

localhost.
my.localnet.hostname
internet.hostname.

How do I alias all these names. So that if program listen to a port on localhost it can  it will be as it it listen on my.localnet.hosname or on
internet.hostname.

The issue came with sendmail local mail delivery. the SMTP port is assigned to my.localnet.hostname. thus I can sendmail. But when I receive mail I use fetchmail, which uses port 25 on localhost (127.0.0.1). becuase of that I get the following error :

fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused

telnet my.localnet.hostname 25    works
telnet localhost 25    fails



Iused to have fedora. This is my first instalation of ubuntu server. I did not have this issue with fedora.

Thanks for any help

-Oz

---

### Post by Iowan on 2009-04-17
localhost is normally tied to 127.0.0.1.  The LAN (local net) hostname typically gets set to 127.0.1.1.  Dunno about the internet hostname - probably in the router... 
localhost will be accessible only from within the same machine (because each (Linux) machine has it's own localhost).

(Not sure if I actually answered your question...)

---

