---
title: "Adding PCi LAN card to motherboard"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by coolecho on 2013-02-05
Hello,

I have Ubuntu 12.04 Installed on a MSI990FXA-GD80V2 AM3+ system. I need to add a 10/100 PCi card to it. Will Ubuntu automatically recognize the new card, or will I have to reinstall Ubuntu?

Thanks

---

### Post by chili555 on 2013-02-05
It will recognize the new card in the sense of 'yes, I see a new PCI device and I'll look for a driver.' All you need do is stick in the card, boot up and it will show up here:```
lspci -nn
```Whether Ubuntu has the driver already depends on the exact card. Do you have a card now or a candidate? What is it?

---

### Post by sudodus on 2013-02-05
Most ethernet cards (wired network connection) can be used out of the box by Ubuntu. This is not true about wireless cards and chips, but it is improving there too.

---

### Post by coolecho on 2013-02-07
I used an older 3COM PCI card and it worked fine. Thanks.

---

