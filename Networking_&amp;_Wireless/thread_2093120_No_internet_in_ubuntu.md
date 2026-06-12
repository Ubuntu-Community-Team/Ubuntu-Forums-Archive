---
title: "No internet in ubuntu"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by clereamusjd123 on 2012-12-10
I have Dell Inspiron 5420 with windows 7. Internet - both wireless and wired work fine on windows. I installed ubuntu 12.04 lately and internet ... neither wireless nor wired work on it. Please help!
 
Maybe the result of this command will help identify the problem: -
```

ifconfig
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14240 (14.2 KB)  TX bytes:14240 (14.2 KB)

```
I noticed that it didn't show me eth0. Why is that so?

---

### Post by Bucky Ball on 2012-12-10
Welcome to the forums. 

> **clereamusjd123 said:**
> I noticed that it didn't show me eth0. Why is that so?

Because it's not recognised and neither is wlan0, your wireless. Try this:

```
sudo lshw -C network
```... and post the result here, please. ;)

(PS: Have you looked in Additional Drivers?)

---

