---
title: "Help with iptables and l7-filter"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by espo on 2011-06-14
Hi all,

im running ubuntu server 11.04, and i got a small problem with l7-filter.

I installed l7-filter-userspace and then i try to test it and used the following iptables command:

```

iptables -t mangle -A POSTROUTING -o ppp0 -m layer7 --l7/proto worldofwarcraft -j MARK --set-mark 1

```

But the command results in this error message:

```

iptables v1.4.10: Couldn't load match `layer7':/lib/xtables/libipt_layer7.so: cannot open shared object file: No such file or directory

```

Can someone help me with this error message?

Greetings
espo

---

