---
title: "DNS Problems."
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by bluewish on 2009-04-30
I set my DNS servers manually, as the ones that are assigned don't work.

The problem is, they always revert back to the ones that don't work.
It can work for 5 mins, 10 mins or even 8 or so hours, but it always changes back.

Is there a way I can set it so it doesn't change back?

---

### Post by x33a on 2009-04-30
i had the same problem.

what i did was, run pppoeconf, when asked to add isp dns servers, choose no.

manually enter the dns servers of your choice in /etc/resolv.conf.

---

### Post by Iowan on 2009-04-30
Static or DHCP address? If DHCP, */etc/dhcp3/dhclient.conf* has a line:```
#prepend domain-name-servers 127.0.0.1;

```that can be changed to put your preferred servers on top of the list.

---

### Post by bluewish on 2009-05-01
> **x33a said:**
> i had the same problem.

what i did was, run pppoeconf, when asked to add isp dns servers, choose no.

manually enter the dns servers of your choice in /etc/resolv.conf.

I just tried that, and it didn't work.. But thanks anyway :)

> **Iowan said:**
> Static or DHCP address? If DHCP, */etc/dhcp3/dhclient.conf* has a line:```
#prepend domain-name-servers 127.0.0.1;

```that can be changed to put your preferred servers on top of the list.

Thanks! That one worked!~

---

