---
title: "Network services definition for ssh"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by dnoyeb on 2008-12-23
Why does the network service definition for ssh in the file /etc/services include 22/udp?  I thought ssh was just over tcp!?

---

### Post by s3gfault on 2008-12-23
ssh does not use the udp protocol, i believe what is happening here is that we are reserving udp traffic on port 22 so that no other application can claim it.

---

### Post by dnoyeb on 2008-12-23
For typo security purposes?

---

