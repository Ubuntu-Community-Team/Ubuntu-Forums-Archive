---
title: "Role of /etc/hosts"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-04-17
Hello,

I have several machines on local network. Laptop#1 can't ping laptop#2 via hostname. I have to check the IPs and add corresponding entries on /etc/hosts file each laptop, in order that they can ping each other via hostname. Can a laptop understand (ping) another laptop via hostname, without the role of /etc/hosts file?


Thanks and regards,

---

### Post by newbie-user on 2012-04-17
Yes, but you have to set up a DNS server to do that. The /etc/hosts file does basic DNS for a single host in the absence of a real DNS server and also acts as a complement to DNS.

---

### Post by rockballad on 2012-04-17
> **newbie-user said:**
> Yes, but you have to set up a DNS server to do that. The /etc/hosts file does basic DNS for a single host in the absence of a real DNS server and also acts as a complement to DNS.

Thank you, it's clear for me now!

---

