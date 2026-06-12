---
title: "Network interface driver initial load problem"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by ceosion on 2010-10-25
Hello all, after several days of trying to fix a problem with my freshly installed Ubuntu 10.10 Server, I found a work around which involves unloading and reloading the driver.

```
sudo modprobe -r 8139too
sudo modprobe 8139too
```

When I do this, it fixes my network card and everything is fine. My question is, why do I have this initial problem to begin with? What would cause the driver to load incorrectly during startup?

The output of ifconfig -a is different from startup and after I reload the driver. Of particular interest, the MAC address is drastically different.

Are there any suggestions for a permanent fix?

Thanks,
-Alex

---

