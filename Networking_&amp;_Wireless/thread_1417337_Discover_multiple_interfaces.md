---
title: "Discover multiple interfaces"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2010-02-27
Is there a way (probably using nmap), to find out what other network interfaces (internal or external) a host has. Given that we know just one of the hosts ip address.

---

### Post by Iowan on 2010-02-27
From the host itself, check **sudo lshw -C network**.

---

### Post by hammad1337 on 2010-02-27
If I had access on the host, even a simple ifconfig would work.
I want to enumerate remotely.

Sorry for not mentioning it clearly before.

---

