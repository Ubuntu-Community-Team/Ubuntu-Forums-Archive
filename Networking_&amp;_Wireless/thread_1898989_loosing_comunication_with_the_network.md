---
title: "loosing comunication with the network"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2011-12-22
Hi, since a few days at work I changed of office, since this day I'm having several problems with all network services: internet, ssh with my server, samba with some machines, etc, checking with some workmates that also use ubuntu they have good response time for those services.

so, my qyestions are.

1. what logs files should I check what is the problem?
2. I'm using wicd as network applet, where can I check my network card speed? and from command line?
3. if I do ping to an internal ip sometimes I don't receive any confirmation, after seconds then the packages have sent to the target ip, what commands/tools should I use to diagnostic my network problem?
4. how can I test my network card?

regards

---

### Post by praseodym on 2011-12-22
Hi,

please show

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

