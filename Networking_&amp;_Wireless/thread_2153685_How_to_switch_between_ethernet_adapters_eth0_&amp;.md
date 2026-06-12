---
title: "How to switch between ethernet adapters eth0 &amp; eth1"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by qroshan on 2013-06-11
How can I switch ethernet adapters (say between eth0 & eth1) easily?

Basically, at work, I want to use my hotspot during personal browsing (eth1) and use the office gigabit network for work purposes (eth0)

Thanks

---

### Post by sanderj on 2013-06-12
Switch the cable?

---

### Post by qroshan on 2013-06-12
> **sanderj said:**
> Switch the cable?

Well, I'm looking for an ubuntu solution (I did ask in an ubuntu forum right?). I can always remove cables.

---

### Post by sanderj on 2013-06-12
> **qroshan said:**
> Well, I'm looking for an ubuntu solution (I did ask in an ubuntu forum right?). I can always remove cables.

What is your definition of "an ubuntu solution"?

---

### Post by scbingham on 2013-06-12
What you are looking to do is routing specific requests, not physically switching. Unfortunately I don't know anything about it but searching info about routing should put you on the right path.

---

### Post by steeldriver on 2013-06-12
... otoh if you *are* talking about manually switching, you should be able to set up 2 separate connections in network-manager, one using each device / interface - there should be a dropdown box in the 'Wired' tab of the connection editor that allows you to select by MAC or interface name (eth0 / eth1)

---

