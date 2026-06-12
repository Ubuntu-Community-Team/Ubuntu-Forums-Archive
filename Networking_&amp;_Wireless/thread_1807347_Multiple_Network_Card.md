---
title: "Multiple Network Card"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by kernel.dead on 2011-07-18
I have 6 network cards in my server, does Ubuntu 11.04 support multiple nics on install? Or will I have to make some config changes to enable the additional 4 currently I have 2 nic's showing up.

---

### Post by jmoorse on 2011-07-19
It should support them unless there are driver issues, can you provide the out of the following please:

```

ifconfig -a
sudo lspci -v

```

---

