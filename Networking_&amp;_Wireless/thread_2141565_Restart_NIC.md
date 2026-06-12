---
title: "Restart NIC"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Vishal Agarwal on 2013-05-03
Hi,
I have two NIC in my server. How can I start one NIC, without disturbing the other one.

Regards,
Vishal Agarwal

---

### Post by SlugSlug on 2013-05-03
```
ifconfig
``` to show whats interfaces then

```
sudo ifconfig eth1 up
```

or ```
sudo ifconfig eth1 down
```

---

### Post by Vishal Agarwal on 2013-05-03
Thanks,
I was thinking the same.

---

