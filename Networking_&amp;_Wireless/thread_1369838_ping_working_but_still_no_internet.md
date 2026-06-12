---
title: "ping working but still no internet"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by rosie'sdad on 2010-01-01
Hi, Sorry total nube here,

I can ping my router, i can ping google and i can ping the ip address you get in the ubuntu help

If i type 192.168.1.1 i can get my router control panel 

i just cant connect to the web,

Any help would be much appreciated.

Thanks

Rob

---

### Post by Iowan on 2010-01-01
Do you ping Google by name or address?
Verify valid nameservers in */etc/resolv.conf*. I presume the gateway is correct, but you can check **route -n** to be sure. Another solution I've seen mentioned is to change MTU value (down from 1500 to 1492). Check it via **ifconfig -a**.

---

