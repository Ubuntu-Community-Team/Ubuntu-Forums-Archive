---
title: "Dns Issues"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Daemn on 2010-01-07
Hi guys,

So I'm having DNS issues (with my router it takes too long to resolve) with 9.10. If I'm using GNOME I can just change the preferences. But where do I find those preferences on the filesystem?

I modified /etc/resolv.conf to just use Google DNS and it works great, but then something overwrites it with my router DNS. I guess that's a generated file, but what do I edit to change the generator?

Thanks in advance

---

### Post by Iowan on 2010-01-07
If you're using DHCP, you can change the "prepend" line in */etc/dhcp3/dhclient.conf*. That *should* put your preferred server(s) at teh top of the list.

---

