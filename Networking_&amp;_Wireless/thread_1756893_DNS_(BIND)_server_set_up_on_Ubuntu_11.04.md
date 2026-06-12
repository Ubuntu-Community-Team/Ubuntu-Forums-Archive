---
title: "DNS (BIND) server set up on Ubuntu 11.04"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by yitzstokes on 2011-05-12
Seeking advice -

Have a DNS (BIND) server set up on Ubuntu 11.04.  The server responds to  nslookups from the localhost or if I am pointed to it from an internal  client.  I have a NAT address through our firewall with port 53 open to  the host.  I can telnet to the server outside the firewall on port 53.   If I try to do any nslookups for a domain that is hosted on this server I  am getting no response.  What have I missed?

rsvp myself and [email]bbazian@mbopartners.com[/email]

---

### Post by collisionystm on 2011-05-12
> **yitzstokes said:**
> Seeking advice -

Have a DNS (BIND) server set up on Ubuntu 11.04.  The server responds to  nslookups from the localhost or if I am pointed to it from an internal  client.  I have a NAT address through our firewall with port 53 open to  the host.  I can telnet to the server outside the firewall on port 53.   If I try to do any nslookups for a domain that is hosted on this server I  am getting no response.  What have I missed?

rsvp myself and [email]bbazian@mbopartners.com[/email]

Is the port set to allow traffic in both directions? Check your firewall logs.

Can you ping ns.domain
Or another entry in your db file?

---

