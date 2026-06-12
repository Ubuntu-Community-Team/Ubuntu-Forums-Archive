---
title: "DNS lookup very slow"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by manusha on 2009-08-30
hi,
DNS lookup in my ubuntu 9.1 is extremely slow. When i inspected the resolv.conf file i got the following content.

```

nameserver 192.168.0.65
nameserver 192.168.0.66
nameserver 222.165.160.18

```

out of these three first 2 are invalid!. I dont know how these entries get here though.

I am using wicd network manager and i have set up it to have one wired connection with static ip anbd i have put the '222.165.160.18' as the dns lookup server ip, which gets appended as the last entry. Could anybody tell me where those other two entries come?

Thanks

---

