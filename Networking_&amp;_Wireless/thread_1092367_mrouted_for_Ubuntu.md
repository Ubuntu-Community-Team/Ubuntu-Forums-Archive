---
title: "mrouted for Ubuntu"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by superdave8000 on 2009-03-10
I'm trying to send out IGMP query packets in order to have my switching environment perform IGMP snooping; however, mrouted doesn't seem to exist in the repositories anymore. Does anyone know what should replace mrouted, or better yet, how I can send the query packets to make snooping work?

-Dave

---

### Post by troglobit on 2010-11-20
The [mrouted]("http://freshmeat.net/projects/mrouted"), or [pimd]("http://freshmeat.net/projects/pimd"), daemons are usually only needed when you want to route multicast traffic between different networks (interfaces).

If all you want is an IGMP querier in your switched network many switches today can act as a querier, as long as they have an IP# assigned to their VLAN interface.

---

