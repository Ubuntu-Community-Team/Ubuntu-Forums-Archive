---
title: "Fitlering Urls through Bind9?"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by jadams_35 on 2009-11-04
Is it possible to filter requests for urls through Bind9 and deny access to sites?

Also, is it possible to pass requests to urls through somekind of website filter software and pass the result off through Binds somehow?

I'm looking to turn mu ubuntu box into a dns server that filters the content throughout my LAN in the house.

Thanks for any thoughts.

jeremiah

---

### Post by ant2ne on 2009-11-04
> **jadams_35 said:**
> Is it possible to filter requests for urls...pass requests to urls through somekind of website filter software and pass the result off...
Are you talking about; a transparent squid proxy using IPcop or dansguardian? I don't know if bind can do that, but squid can.

---

### Post by jadams_35 on 2009-11-04
I'm looking to point all the machines on my LAN to one central location. The central location does all the filtering and forwarding. I don't really want to manage each machine. It is a mixed os lan.

---

### Post by ant2ne on 2009-11-08
a transparent squid proxy using IPcop or dansguardian.

---

