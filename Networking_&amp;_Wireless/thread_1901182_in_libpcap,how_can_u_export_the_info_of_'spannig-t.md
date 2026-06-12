---
title: "in libpcap,how can u export the info of 'spannig-tree protocol ' from a packet??"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by xazq08 on 2011-12-28
[SIZE="3"]i've had a code done that it can get the info of 'ethernet' 'ip' 'tcp'and export the fileds of them.

but how for 'stp',i knew its protocol:0x0026,and then??

thanks~[/SIZE]

---

### Post by bvkmohan on 2011-12-28
Does the environment where you executed your code actually has STP traffic ? check with wireshark for STP traffic. Some switched networks use RSTP instead which uses port 554.

---

### Post by xazq08 on 2011-12-29
> **bvkmohan said:**
> Does the environment where you executed your code actually has STP traffic ? check with wireshark for STP traffic. Some switched networks use RSTP instead which uses port 554.

thanks!
i had stp exactly in my packet.
i worked it out with the help of wireshark and i had the code done a few minutes ago.:D

---

