---
title: "Lost Eth0 on wire to Router"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by Rodney9 on 2010-04-22
Hello, 
My 9.10 has lost it connection to my router.

Lucid finds it ok as Auto ethO , XP gets on the net ok as well

How do I fix Karmic ?

 I click on network, it is greyed out but still lets me  edit connections and add wired as auto etho but still no connection.

Not sure what else to do ?

ifconfig -a shows -
```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:20:1b:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Rodney

---

### Post by dineshs on 2010-04-22
Can you check
/etc/NetworkManager/nm-system-settings.conf 

I understand that the file should be```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```
for NM to manage ethernet.Not sure

---

### Post by Rodney9 on 2010-04-22
> **dineshs said:**
> Can you check
/etc/NetworkManager/nm-system-settings.conf 

I understand that the file should be```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```
for NM to manage ethernet.Not sure

Thank You , it said 'false' changed it to 'true'
it is all working now , Thank You !

---

### Post by Hiankun on 2010-12-12
I just encountered the similar problem. Your method works for me. Thank you. :-)

---

