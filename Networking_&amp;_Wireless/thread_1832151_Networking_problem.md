---
title: "Networking problem"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by inhuman!!! on 2011-08-24
Recently I changed my Internet provider form a wireless PPoE to Wimax. 
Problem is my Wimax CPE and wireless router do not work with each other.
I can connect to with direct cable to Wimax and I also have my network when connected to router but can't have the both :confused:
Both devices have DHCP and I tried turning off each of them but no use.
I know its not Ubuntu related but I need help.

---

### Post by praseodym on 2011-08-24
Hello,

please show the following outputs:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
iwconfig
rfkill list
lsmod
lspci -nnk | grep -iA2 net
```

---

### Post by inhuman!!! on 2011-08-24
OK, SOLVED 
I had to disable DHCP in my router and change its role to just an accesspoint. So my Wimax CPE would be the DHCP and router.

---

