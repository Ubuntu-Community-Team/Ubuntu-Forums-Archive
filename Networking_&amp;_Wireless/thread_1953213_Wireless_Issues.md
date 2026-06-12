---
title: "Wireless Issues"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by aorwin on 2012-04-05
Hello and thank you in advance for your time,

I have just installed Ubuntu 10.04 64-bit on my desktop and upon logging in am unable to connect to my ethernet device. I have no possibility of wireless internet. It seems Ubuntu did not configure my eth0 automatically. I am unable to configure this myself.00

I had previously used 10.04 as well as 11 on my laptop and it was working flawlessly. Can anyone help me out please?

Thank you and regards,

Lex

---

### Post by praseodym on 2012-04-06
Hi,

please show the outputs of

```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
lsmod
```
How do you want to connect? Router, modem, or combination of these?

---

