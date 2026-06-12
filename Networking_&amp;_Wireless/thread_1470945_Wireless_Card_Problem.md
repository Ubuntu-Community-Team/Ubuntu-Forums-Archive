---
title: "Wireless Card Problem"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by sean360 on 2010-05-03
Hi, I've upgraded from ubuntu 9.10 to 10.04. My wireless card has been working fine on 9.10, but since upgrading to 10.04, the card is not being detected anymore. If I plug in a USB wireless card, it works and will log into my wireless network. It is a desktop (Advent T9102). The card is a Creatix 405 PCI 802.11g.

If anyone knows where I could find drivers for this card, or how to solve this problem, it will be greatly appreciated. Thanks

---

### Post by coffeecat on 2010-05-03
> **sean360 said:**
>  The card is a Creatix 405 PCI 802.11g.

The first thing to do is to find out which wireless chipset it uses. Open a terminal and post the output of:

```
lspci
```

---

