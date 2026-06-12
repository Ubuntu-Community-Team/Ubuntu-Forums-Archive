---
title: "Wireless not working, but worked in Ubuntu"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by rknetsch on 2010-01-06
I downloaded Ubuntu and was not having luck running from a USB stick, so I decided to go the Wubi route.  The Ubuntu I downloaded saw my wireless fine and everything, but the Kubuntu I now have under Wubi does not see my wireless at all.  Does that mean I have to go the whole ndiswrapper route?

---

### Post by Crafty Kisses on 2010-01-08
> **rknetsch said:**
> Does that mean I have to go the whole ndiswrapper route?
Not necessarily, depending on what card you have it may be fairly easy to fix the issue at hand, and in some cases you're going to have use ndiswrapper, but using ndiswrapper is very simple. First I need a couple things from you, so run these commands and post them back here at the forums, so run:
```
lspci
lsusb
lshw -C network
```

---

### Post by rknetsch on 2010-01-09
Thanks for your help.  I deem to have fixed it by installing the driver software.

---

