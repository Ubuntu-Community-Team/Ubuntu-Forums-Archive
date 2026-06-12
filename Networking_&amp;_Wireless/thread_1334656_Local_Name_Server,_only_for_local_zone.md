---
title: "Local Name Server, only for local zone"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Razorg on 2009-11-22
Hello all,

What i need is having a local name server, to resolve local hostnames.
Its of no real usage, but im experimenting, in order to do it later in a larger scale.

My router ( gateway to the internet ) is automatically recieving dns information from the ISP uppon connection, and itself acts as a dns forwarder. I have setup a dns server on the local network that will resolve say domains ".home". I have done this with bind, but my problem is that i don't know how to let my computer know to ask the local nameserver only for the ".home" domain. for everything else, ask the router.

Any idea?

---

### Post by Razorg on 2009-11-23
Noone?

---

### Post by Iowan on 2009-11-23
I like **dnsmasq** for a small network (mine). It has the option to specify a domain (I presume that's the domain over which it has authority). I'm not sure how it's done in **bind**.

---

### Post by Razorg on 2009-11-23
Thanks for your reply.

The DNS server is up and running. My problem is that i want to specify to a client PC, to query the local DNS server, ONLY for domains e.g. ending in ".home"

---

