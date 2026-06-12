---
title: "wireless adapter  problem"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by christophar1 on 2009-05-01
I am new to Ubuntu. Trying to install it on an Ibm ThinkPad with
a USR5411 pcmcia card. Does not see the card. Any suggestions on
what to do to get it working. Thanks, Christophar

---

### Post by chili555 on 2009-05-01
How about letting us see, from a terminal:```
lspcmcia
sudo lshw -C network
```With the card jammed in the slot, of course. I'll bet you see the word 'Broadcom' somewhere.

---

