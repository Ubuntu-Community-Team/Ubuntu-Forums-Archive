---
title: "register fixed ip in router for dns"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by copycat on 2009-01-20
Hi,

I'm a ubuntu user from version 5.  I've searched a lot on networking fora without result.  So her is my question. On a new VM 8.04 I'm installing (or let's say try) Zimbra. Resolving is really important for this mailserver.
I found that ... when I set a static ip in my interfaces file, my router (WAG325N from linksys) replies with my old ipadress on a nslookup/dig.  Is there a way to make my router understand I do have a new fixed ip? Ping works fine and replies with 127.0.0.1.
I have a non-dhcp range from x.x.x.0-50 and my static ip ends with 22. My router always answers with the fault x.x.x.53 on a nslookup.
The resolve.conf is set (nameserver router-ip).

Thanks:popcorn:

---

### Post by Iowan on 2009-01-20
One option would be to let the router assign a static lease of .22 based on MAC address.

---

### Post by copycat on 2009-01-21
> **Iowan said:**
> One option would be to let the router assign a static lease of .22 based on MAC address.


Hey, id it would be a nice solution. Thanks for the reply.

Problem is that I have more VM servers with a fixed address. 

With a older firmware you could telnet to the router.  Now it isn't possible anymore. 

There is no way to register your "A records".  The only workaround I can find is set up a bind dns server.  But that is quiet heavy for a resolving problem.

---

