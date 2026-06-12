---
title: "Network issue after recent update?"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by davrosuk on 2010-09-04
After doing a big round of updates on 10.10 Beta in the last 24 hours (and noticing some X updates in the mix) I thought I'd do a restart. Post-boot I noticed that I hadn't got a DHCP address from my server. After a few minutes I came up with a workaround:

```
ifconfig eth0 up
dhclient

```

What I wanted to know is - is anyone else having this issue? or is this just me? I know it was working pre-updates...

---

### Post by davrosuk on 2010-09-04
Alas, I should have spotted that "connect automatically" was unchecked. Why the update should do this I don't know, but it did. Sorted.

---

