---
title: "squid+dansguardian=no speed limits"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by W03L on 2011-06-20
Hi.

there is squid+dansguardian on the server. Content filtering is working but IP speed limits is not. squid log have only 127.0.0.1 address for all. if dansguardian is removed then it is all ok.
I'm try to add ```
cache_peer 127.0.0.1 parent 8085 0 no-query no-digest no-netdb-exchange default
``` in squid.conf but no effects is.

please, help me with this.

---

