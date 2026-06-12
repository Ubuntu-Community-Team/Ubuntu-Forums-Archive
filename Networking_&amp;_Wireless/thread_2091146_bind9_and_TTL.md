---
title: "bind9 and TTL"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by Nevstah on 2012-12-04
hi guys

so everythings installed and outwardly working properly

i've created a master zone for my domain to resolve locally. i've added hostnames with IP addresses and these resolve as you would expect

however if i 'dig fileserver' i get the expected reply with a local IP address, but the TTL always remains the same '3600'

whereas if i 'dig google.com' or any other real domain, i get  ever lower TTL's

but i dont see what i've done wrong! or is this normal for a 'local' dns server?

cheers in advance

nevstah

---

