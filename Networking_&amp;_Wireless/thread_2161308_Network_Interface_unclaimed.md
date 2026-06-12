---
title: "Network Interface unclaimed"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by Webdawgz on 2013-07-10
The network interface appears to be unclaimed. I cannot do any updated or install any packages. This is so frustrating but i want to learn about LINUX please.
If I need to edit some config files please forward me the commands and i will try and do my best. I ve been googling for the last 2 days just trying to get my network card to work.
Ubuntu documentation is very basic.
Ubuntu 10.04 is the version. Please help Windows Expert in stress.

---

### Post by praseodym on 2013-07-10
Hi,

please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
iwconfig
```
You know that 10.04 is outdated (for desktop systems, not for servers)?

---

### Post by Webdawgz on 2014-02-09
Hi pras 
I took your advice and upgraded to version 13.10 and all up and running. How do I close the thread?

---

