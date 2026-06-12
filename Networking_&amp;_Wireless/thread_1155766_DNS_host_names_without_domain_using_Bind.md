---
title: "DNS host names without domain using Bind"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by onlyteo on 2009-05-11
Hey ninjas!
On the LAN i operate there are several servers and workstations which all uses a Linux/Bind box as the primary DNS server. I want to assign all machines on the LAN host names, but without any domain name part. So i want Bind to resolve e.g. 'myserver1' to the IP of one of the servers, so i will be able to write //myserver in order to access that box.

How do i configure that in Bind? Do i need to set up a zone for each host, or can i put the host names in a single zone (like i would if i used a domain)? If so, which zone?

---

