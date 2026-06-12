---
title: "Physical address for ethernet adaptor"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by RiazM on 2010-08-26
Hi there, I've just arrived at uni and to set up my wifi apparently I need my "media access control which is listed as the phsyical address for ethernet adaptor local area connection." on windows you can find it by using the command ipconfig /all but that didn't work when i put it into terminal.

Could anyone provide me with an equivalent command?

---

### Post by DFlame on 2010-08-26
A number of ways you can get your MAC :)

If it's a laptop, it will usually be printed somewhere on the bottom of the system.

You can also find it by entering ```
ifconfig
``` in a Terminal window. This gives an output like...

```
wlan1     Link encap:Ethernet  **HWaddr 00:00:00:00:00:00**  
          inet addr:xxx.xxx.x.xx  Bcast:xxx.xxx.x.xxx  Mask:xxx.xxx.xxx.x
          inet6 addr: fxxxxxxxxxxxxxxxxxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:414880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:541818142 (541.8 MB)  TX bytes:34188700 (34.1 MB)
```

You're looking for the HWaddr in this case (I've blanked mine out for security purposes).

---

