---
title: "Domain name for LAN should be?"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2009-05-14
I'm helping the local Boys and Girls Club set up a server and their ancient Cisco router has their internal network set to youth.local however their website is at [http://www.bgcfc.org](http://www.bgcfc.org) but it's being hosted somewhere else.  Should I set the domain name to bgcfc.org for the user on the internal network?

---

### Post by netztier on 2009-05-14
> **matthewboh said:**
> I'm helping the local Boys and Girls Club set up a server and their ancient Cisco router has their internal network set to youth.local however their website is at [http://www.bgcfc.org](http://www.bgcfc.org) but it's being hosted somewhere else.  Should I set the domain name to bgcfc.org for the user on the internal network?


Using **.local** as domain name can have some side effects, especially when local DNS servers come into play:

[Zeroconf]("http://en.wikipedia.org/wiki/Zeroconf") networking uses **.local** as its toplevel domain. Zeroconf enabled systems can reference each other via **<hostname>.local**, circumventing the need to have a local DNS server. Ubuntu uses [Avahi]("http://www.avahi.org/"), a Zeroconf implementation used on many platforms (side note: Apple call their implementation "Bonjour").

Avahi will [disable itself]("http://www.avahi.org/wiki/AvahiAndUnicastDotLocal") when it discovers that there's a DNS server around that answers queries for names in **.local**, hence the recommendation not to use .local .

What you could do is use a subdomain of bgcfc.org, like ***local*.bgcfc.org** or ***internal*.bgcfc.org**, but don't assign the same (upper-level) domain that is being used/hosted externally. If you do, things don't get broken, but there'll be twists and turns to take once someone comes up with the idea or an actual use case for running a local DNS on the internal LAN while keeping the same domain name.

Having the internal systems in a subdomain (and the local names that they might be using/resolving in the future, such as a hypothetical "intranet.local.bgcfc.org") will not harm the accessibility (or "resolveability", in the context of DNS and Domain Names) of names in the upper-level domain (such as [www.bgcfc.org](www.bgcfc.org)). The upper-level domain can still be hosted on external DNSs, while the local (subdomain-)names can/should be hosted on an internal DNS.

best regards

Marc

---

