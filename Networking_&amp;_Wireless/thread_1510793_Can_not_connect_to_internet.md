---
title: "Can not connect to internet"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by susankhya on 2010-06-16
Friends,
 
I downloaded and installed Ubuntu 10.0.4 LST.
 
But it can not connect to the internet or LAN.
 
My nic card is:  Inte(R) PRO/100 VE
 
How to configure it ?
 
Thanx in advance
 
Rajan Dahal
School of Computer Studies (SCS)
Kathmandu
NEPAL
 
[COLOR=red]NB:  But the internet connection works fine when I run the ISO image from VMWare Player.[/COLOR]

---

### Post by dineshs on 2010-06-16
Do you have a modem/router connected via ethernet?
What is the result of
```
ifconfig -a
```

---

### Post by Iowan on 2010-06-16
From a terminal (Applications>Accessories>Terminal), **sudo lshw -C network** should provide some other details about your interface - if the aforementioned **ifconfig -a** doesn't show an IP address...

---

