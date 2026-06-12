---
title: "no internet"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by tsq on 2011-08-29
i can connect to any LAN IP from IP2, except to gateway (& internet)
i can connect from any LAN IP to IP2, except from gateway 

@gateway ]# iptables -L -n|grep $IP2
( Chain INPUT (policy DROP) )
ACCEPT     all  --  $IP2          0.0.0.0/0

no iptables @IP2, i removed rules, later uninstalled iptables
computer
pc @IP2 has 2 eth cards, no diff in using either
i was extremely keen to get wake on lan working, could i have maybe messed sth up w ether-wake, wakeonlan, arp ..(?)

could someone please help me with this

---

### Post by northd_tech on 2011-08-29
It would probably help to first know which type(s) of network hardware you are using (there likely could be issues there, especially if you just installed or upgraded to Ubuntu 11.04 or newer).

Can you post the output from the following terminal commands:

```
lspci | egrep 'etwork|thernet'
sudo lshw -C network
lsmod
lsusb
ifconfig -a
iwconfig
```

---

