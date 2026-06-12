---
title: "How to forbidden one Network Card in Ubuntu?"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by fanquan on 2009-12-24
My PC have two network cards, I installed Ubuntu8.04, but the Network Card seems not have a stable work(intermittence while power on PC every time). So I want to forbid one Network Card, but don't kown how to do this.Is there have some way to do this?

---

### Post by Iowan on 2009-12-25
Are the cards (either or both) built-in, or add-on? Built-in's might have a BIOS option to disable them. Otherwise, there are some tricks (and probably better ways) to control them.

One such trick is to define the problem card in */etc/network/interfaces* something like:```
iface eth0 inet manual

```The problem with tricks is they don't always work.
(If you need help editing the file, please ask!)

---

### Post by ant2ne on 2009-12-25
> **Iowan said:**
> ```
iface eth0 inet manual

```The problem with tricks is they don't always work.I don't like this idea as the higher levels may still try to push data out this interface.

The best way to do this would be disable it in the bios or run a start up script with...
```
sudo ifconfig ethX down
```
(where X is the number to the faulty interface. usually eth0 or eth1) Maybe add a line to /etc/rc.local

---

