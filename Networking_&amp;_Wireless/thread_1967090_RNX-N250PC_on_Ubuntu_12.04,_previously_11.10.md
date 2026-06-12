---
title: "RNX-N250PC on Ubuntu 12.04, previously 11.10"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by virtuo on 2012-04-27
RNX-N250PC on Ubuntu 11.10
Hi:

Been an Ubuntu user for a few years now and have been wired, just purchased a router with wireless card. The Rosewill RNX-N250 PC is what I have and I installed it, but cannot get a connection to the router with my computer. The router is connected to DSL on another computer, in the other room and I can get a wireless connection via my smart phone no problem. Any help?

---

### Post by praseodym on 2012-04-28
Hi,

please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Checked, if a MAC-filter is turned on in your router?

---

