---
title: "Ethernet Card wont Work even though its showing up in lspci"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by jonnie2004jonniesweb on 2009-03-09
Hello, I have set up a machine that runs Ubuntu Server 8.10. I don't have any Gui set up. My problem is that my network card doesn't work so i cant do any network related tasks.

I ran lspci and found this related to the Ethernet adapter:

```
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
```


Note: I have a beginners grasp of basic tasks that you would do in Ubuntu. If any other things are required just ask.

---

### Post by Iowan on 2009-03-10
Check to see if the card has an alias (eth0):```
lshw -C network
```Then see if it has an IP address:```
ifconfig -a
```
Is it set up with static or DHCP address?

---

