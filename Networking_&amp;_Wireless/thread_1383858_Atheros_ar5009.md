---
title: "Atheros ar5009"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by x_iOwn_x on 2010-01-17
Hi im really new to ubuntu and i was wondering how to get the above wifi card working as it is not supported. Thanks :D

---

### Post by The Toxic Mite on 2010-01-17
Hey! I know that you know the wireless card's model no., but can you give us more detail please?

Applications --> Accessories --> Terminal

```

lspci -v less
sudo lshw -c network
iwconfig
dmesg

```

Paste the outputs here when done :)

---

