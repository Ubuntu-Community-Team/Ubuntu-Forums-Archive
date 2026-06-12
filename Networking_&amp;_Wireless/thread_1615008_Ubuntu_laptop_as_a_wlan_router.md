---
title: "Ubuntu laptop as a wlan router"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by LonelyStar on 2010-11-06
Hi,

Because my internet provider did not send me the wlan router yet, I am trying to configure a laptop running ubuntu as a wlan router.
I added a ad-hoc network and set under IPv4 settings the "Methode" to manual.
Now I am trying to connect with the computers of my friends. They all run windows. They connect fine to the Network, but they do not receive an IP from the dhcp server. Strange, because the dhcp server seems to run fine ...

Any advice?

Thanks!
nathan

---

### Post by spiky001 on 2010-11-06
Have you tried assigning the ip addresses on the win machines? i,e 192.168.1.1 is your lappy set the others 192.168.1.2 etc  Have you tried setting your lappy connection to shared with other pc?

---

### Post by LonelyStar on 2010-11-06
I must appologize, I said something wrong in the original post. I did not set the methode to "Manual" but to "Shared with outher computers" (as suggest).

Now I found out something new: It works when I disable security.
When I enable security (i.E. WEP), the windows computers connect but do not get an IP address.

What could that be?

Thanks!
Nathan

---

