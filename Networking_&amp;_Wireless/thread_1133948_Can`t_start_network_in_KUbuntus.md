---
title: "Can`t start network in K/Ubuntus"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by 6ex on 2009-04-23
I want to use Ubuntu, but I can`t make my network work!

It works in: Kubuntu 7.10, Slackware 12.2, Debian 4.0
It doesn`t work in: Kubuntu 8.04,8.10 , Ubuntu 9.04-livecd, Debian 5.0 Slackware-current

Problem description:
**NetworkManager** says, that it can`t establish connection, but detects if the cable pluged in. I try to configure network using **/etc/network/interfaces**  or **ifconfig**.** ifconfig** output seems Ok - correct address & netmask, but my router & notebook still don`t ping.
If I try **dhclient** is says something like: "there is no dhcp server".

PS: May be it`s because of kernel configuration. In Slackware 12.2 - kernel 2.6.28 (same as in Ubuntu 9.4) network worked fine, but when I upgraded it to Slackware-current - kernel 2.6.29 there were the problem.
-------------------
Motherboard: ASUS P5N32-E SLI PLUS

---

### Post by 6ex on 2009-04-23
Tried this:
```
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
```

Works with Slackware-current (kernel 2.6.29), but doesn`t work with Ubuntu 9.04

---

### Post by 6ex on 2009-05-07
After that have to run this:
```

update-initramfs -u -k $(uname -r)

```

---

