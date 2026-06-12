---
title: "tough book cf-48"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by ibootindos on 2009-08-06
I got a reworked toughbook cf-48, loaded jaunty onto it, and now it won't recgonize the onboard wireless card?

---

### Post by prshah on 2009-08-06
> **ibootindos said:**
> I got a reworked toughbook cf-48, loaded jaunty onto it, and now it won't recgonize the onboard wireless card?

What make/model/brand is the onboard wireless card?```
lspci | grep -i -E wireless\|ethernet
``` in a terminal (Applications-Accessories-Terminal) will give you the information.

If you can't find it in lspci, it may be a USB card; see ```
lsusb
```

---

