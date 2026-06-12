---
title: "IP Assigning Network Problem"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by adnan666 on 2009-05-13
After Assigning IP Manually Network Cannot Be Accessed.

Kindly Suggest A Solution...

---

### Post by Peter09 on 2009-05-13
Can you post the output of 

```
ifconfig
```

and

```
route
```

---

### Post by Iowan on 2009-05-13
Manual IP via NM or via */etc/network/interfaces* edit? The interfaces file will also require gateway address, and you will need to manually set your DNS server and (optionally) search domain in */etc/resolv.conf*.

---

