---
title: "Compaq Presario c750BR Notebook PC"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by Maymel on 2011-08-30
I installed Ubuntu 11.4 on my notebook more I can not open a connection to my data, tried to find the knetworkmanager to try to open a network connection as I had explained I can not ... Can someone give me a light ...
I need a detailed explanation, I have no knowledge in computer

---

### Post by praseodym on 2011-08-31
Hello,

please open a "terminal" and copy&paste the following commands into it:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Please post the outputs

---

