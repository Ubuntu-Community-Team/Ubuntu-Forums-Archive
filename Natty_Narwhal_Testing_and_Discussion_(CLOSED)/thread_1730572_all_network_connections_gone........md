---
title: "all network connections gone......."
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by reikidude on 2011-04-16
ost all my network connections after upgrading from 10.10 to 11.04. the laptop is an Dell insperion 1501 with an ADM Turion64 

iwconfig says "no wireless extentions"

I did a upgrade earlier on an AMD athlon 2.4ghz and everything runs absolutely beautiful

suggestions anyone?

regards, Martijn.

---

### Post by dino99 on 2011-04-16
might be related to this wifi chipset: google around it (natty+yourchipsetname)

sudo ifconfig

---

### Post by reikidude on 2011-04-16
After i typed ifconfig the output was this:

lo       Link encap:local loopback
         inet addr:127.0.0.1  Mask:225.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:3408 errors:0 dropped:0 overruns:0 frame:0
         TX packets:3408 errors:0 dropped:0 overruns:0 carriers:0
         collisions:0 txqueulen:0
         RX bytes 272288 (272.2 KB)  TX bytes: 272288 (272.2 KB)

my processor is an ADM turion 64 mobile technology.

I am still newby and use Ubuntu mainly because it works usually totally awesome...!
 Thanks guys,

Martijn

---

### Post by 5149.5 on 2011-04-16
Try this command. It will provide information for people to help you.
```

sudo lspci -nnk | grep -i wireless
```

---

