---
title: "New computer, no wireless"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2012-08-21
Just built my first computer. Booted up and everything is working but it is not finding my network. I installed a hard drive from my old computer, running Ubuntu 11.10. It shows my network still, but the wireless tab at the top of the screen does not recognize it. Any tips on how to proceed with debugging and fix? Thanks.

---

### Post by Kirk Schnable on 2012-08-22
I'm not sure I'm clear on what your issue is...

It might help us help you if you can supply us with the output from these commands:

```
sudo lshw -C network
```

```
iwconfig
```

Then we can take a crack at some other ideas to narrow your issue down.
Kirk

---

