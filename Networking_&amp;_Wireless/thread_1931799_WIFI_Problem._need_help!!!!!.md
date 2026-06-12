---
title: "WIFI Problem. need help!!!!!"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by pandusati on 2012-02-26
Hi

my laptop is 10 day old. i have installed ubuntu10.10 and by WIFI im using the internet but last two day my laptop showing the wifi network is connect but while browsing the browser shows "Server not found" for all website. i'm curious to know the reason.

---

### Post by hansum_rahul on 2012-02-26
Can you ping a known url and see if it actually pings?

try: ping 8.8.8.8

If it does, then it is probably a nameserver issue and you need to add a nameserver (like say, 8.8.8.8).

---

### Post by pandusati on 2012-02-26
Thanks Yeah!!! it is pinging correctly then what is the reason i'm not understanding

---

### Post by praseodym on 2012-02-26
Hi,

Ubuntu 10.10 is only supported until april 2012.

Please show the outputs of

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

