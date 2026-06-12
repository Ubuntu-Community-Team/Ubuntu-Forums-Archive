---
title: "New Motherboard eth1. Need to change to etho"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Hurons on 2008-12-29
Hello All,

Just installed the new motherboard into an exsisinting satable 8.10 system and it loaded flawlessly. However, the nic card is eth1 and I need it to revert back to eth0. I am having a hard time figuring it out.  

Please help me out.

Thank you and happy holidays.

---

### Post by albandy on 2008-12-29
edit /etc/udev/rules.d/70-persistent-net and modify it. simply changes entries from eth0 to eth1 and eth1 to eth0

---

### Post by Hurons on 2008-12-29
> **albandy said:**
> edit /etc/udev/rules.d/70-persistent-net and modify it. simply changes entries from eth0 to eth1 and eth1 to eth0

Thanks..

---

### Post by kkady32 on 2009-04-27
Thanks..

---

