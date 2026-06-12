---
title: "10/100 speed configuring."
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by Majes on 2006-04-18
Hi all!

Before saying anything I would like to thank all the ubuntu community for being as it is.

Im spanish, so ill try to do as my best to explain my situation in english.

I have a router with a speed of only 10 full duplex, and a network pci card(eth0) (the typical realtek rtl8139) with a speed of 10/100.

How can I configure the eth0 speed to 10 full duplex?

I have it set to auto now.

Thanks!

---

### Post by fdoving on 2006-04-18
Hi.

Use 'mii-tool'

Example:
```

sudo mii-tool -F 10baseT-FD eth0

```
This will force 10baseT-FX on eth0.


For more information on mii-tool:
```

man mii-tool

```

- Frode

---

### Post by Majes on 2006-04-19
hm...

does it ship with ubuntu ?

---

### Post by Majes on 2006-04-19
yes, it does, thanks a lot, it solved my problem ^^

---

