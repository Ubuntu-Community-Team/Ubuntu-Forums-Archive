---
title: "wired LAN not connecting  in compaq presario C702 laptop"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by jayaveldp on 2012-02-01
Dear All,
           I have compaq presario C702 laptop and installed ubuntu 10.03. I am trying to connect internet through a LAN network. I am new to linux and I am not able to connect to the network. I am not able to identify the problem. Below is the observation
1. I saw a network connection icon in the top right marked with red.
2. My network is limited by 10MSPS full duplex.

I want to configure my network card setting with this value and connect to the network. Pl advice.

Jayavel

---

### Post by praseodym on 2012-02-01
Hi,

please show the terminal (CTRL+ALT+T) outputs of the following commands:

```
lspci -nnk
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lsmod
```
Do you have wireless working?

---

