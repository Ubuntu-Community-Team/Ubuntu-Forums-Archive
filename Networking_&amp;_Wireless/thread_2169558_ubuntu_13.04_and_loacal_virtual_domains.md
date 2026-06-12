---
title: "ubuntu 13.04 and loacal virtual domains?"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by shamsat on 2013-08-22
I am running the ubuntu 13.04 with apach2 web server  and have 5 virutal domains, the pc get it's private ip from the ADSL router, i didn't find any dns server to add these domains for local web server?

---

### Post by newbie-user on 2013-08-23
You need to install a DNS server. You can use BIND or DNSmasq.

---

### Post by Cheesemill on 2013-08-23
Or you can use the easy method and just add a line to /etc/hosts for each of your domains.

---

### Post by newbie-user on 2013-08-23
> **Cheesemill said:**
> Or you can use the easy method and just add a line to /etc/hosts for each of your domains.

:)  Yes, you could do that too. I suppose for testing that would be the best way to do it.

---

