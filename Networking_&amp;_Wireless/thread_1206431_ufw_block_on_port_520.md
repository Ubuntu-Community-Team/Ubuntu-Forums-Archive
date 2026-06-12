---
title: "ufw block on port 520"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by vmalmedy on 2009-07-07
Hi,

I've installed UFW a few days ago and tried to configure it.
I however receive a lot of messages like
```
Jul  7 10:03:35 pc_name kernel: [347317.216668] [UFW BLOCK] IN=eth0 OUT= MAC=xxx SRC=my_ip_adress DST=255.255.255.255 LEN=532 TOS=0x00 PREC=0xC0 TTL=2 ID=0 PROTO=UDP SPT=520 DPT=520 LEN=512
```

What can I do?

---

### Post by superprash2003 on 2009-07-07
if you want to open that port , then go ahead and open it.. then those messages would stop displaying!!

---

### Post by DGortze380 on 2009-07-07
> **vmalmedy said:**
> Hi,

I've installed UFW a few days ago and tried to configure it.
I however receive a lot of messages like
```
Jul  7 10:03:35 pc_name kernel: [347317.216668] [UFW BLOCK] IN=eth0 OUT= MAC=xxx SRC=my_ip_adress DST=255.255.255.255 LEN=532 TOS=0x00 PREC=0xC0 TTL=2 ID=0 PROTO=UDP SPT=520 DPT=520 LEN=512
```

What can I do?

Looks like UDP on port 520 is used for RIP and Timeserver. 
Be aware of the following information: Ramen port 520 (UDP) - A UDP backdoor ([http://www.proxyblind.org/trojan.shtml](http://www.proxyblind.org/trojan.shtml))

IMO it's safe to open the port for UDP traffic if you really want. But if you're receiving no adverse effects from the blocked traffic, I'd just leave it closed.

---

