---
title: "Peerdns"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by moonpup on 2009-05-26
In Redhat/Fedora you could specify peerdns=no in the /etc/sysconfig/network-scripts/ifcfg-ethx file. Is there a similar file in Ubuntu where i could put this variable setting?

I need to stop ubuntu from overwriting the /etc/resolv.conf because of dhcp.

---

### Post by Iowan on 2009-05-26
What is getting overwritten- DNS servers? There's an option in /etc/dhcp3/dhclient.conf :```
#prepend domain-name-servers 127.0.0.1;

```than can be used to put your preferred servers at the top of the list.

Or am I missing the problem?

---

### Post by moonpup on 2009-05-26
Thanks, that puts my preferred server at the top of the list but I still lose my search variable.

ex: search test.com

I really need /etc/resolv.conf to not be modified by DHCP at all. Yes, I know I could just set a static ip, but this peerdns variable on Redhat systems was such a simple fix.

---

### Post by moonpup on 2009-05-26
Got it...

the 'supersede domain-name' variable setting forced my selection.

---

### Post by Iowan on 2009-05-26
I was gonna suggest changing a setting in /etc/dhcp3/dhclient.conf, but I didn't see a good one to effect the results you desired - glad you found it.

---

### Post by ningji on 2012-01-13
what happens if i have eth0 and eth1,
both static, both has its own DNS, can it still work ?

how about 1 dhcp, 1 static ?


> **moonpup said:**
> Got it...

the 'supersede domain-name' variable setting forced my selection.

---

