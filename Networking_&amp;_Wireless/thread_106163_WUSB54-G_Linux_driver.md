---
title: "WUSB54-G Linux driver"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by Picatta on 2005-12-20
I was wondering if there was a linux driver for my WUSB54-G device.  I tried google, and I got lots of dead links and 15-30 day trials.  NDISWRAPPER didn't work, either.

---

### Post by Lambert on 2005-12-20
There's at least two different chipsets for this device depending on version(ralink or prism54). So driver depends on which chipset you have.

Run this command and see if there's information on which one it is.

```
lsusb -v
```

---

