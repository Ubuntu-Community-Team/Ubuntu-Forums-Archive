---
title: "speed and duplex"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by sjefsape on 2009-03-11
Can anybody tell me why I only get 10mbit half duplex ?
Both NIC and router supports 100mbit full duplex..
Is 40 meters of cable from NIC to router.
Bad cable?

---

### Post by cariboo on 2009-03-11
THe maximum length of a network cable can be 100 meters, so that shouldn't be a problem. Have you tried ethtool to change you nic settings? It is available in the repositories.

Jim

---

### Post by terazen on 2009-03-11
If one side is set to 100/full duplex and the other is auto-negotiate then the auto-negotiate side goes to half-duplex pretty much every time.  Gotta either set the router to auto or the pc to 100/full.

---

### Post by sjefsape on 2009-03-11
> **terazen said:**
> If one side is set to 100/full duplex and the other is auto-negotiate then the auto-negotiate side goes to half-duplex pretty much every time.  Gotta either set the router to auto or the pc to 100/full.

Can`t find duplex settings on my router. It is a WRT54G

---

