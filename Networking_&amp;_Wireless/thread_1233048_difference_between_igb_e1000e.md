---
title: "difference between igb e1000e"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by ronelly on 2009-08-06
Hi all,

I am trying to find out exactly which network driver is used on my machine for the netw. card. I searched dmesg and here is what i found:

e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k4
e1000e: Copyright (c) 1999-2008 Intel Corporation.
...
Intel(R) Gigabit Ethernet Network Driver - version 1.2.45-k2
Copyright (c) 2008 Intel Corporation.
ixgbe: Intel(R) 10 Gigabit PCI Express Network Driver - version 1.3.56.5-NAPI
Copyright (c) 1999-2008 Intel Corporation.

As far as I can understand it uses the e1000e and igb (Intel(R) Gigabit Ethernet Network Driver - version 1.2.45-k2). But to my understanding it should be only one network driver that should be in use. Can someone maybe explain the difference between e1000e and igb and how exactly everything works with this drivers issue? Or a hint to an address where I could look it up.

Appreciate any help.
Cheers,
Elli

---

