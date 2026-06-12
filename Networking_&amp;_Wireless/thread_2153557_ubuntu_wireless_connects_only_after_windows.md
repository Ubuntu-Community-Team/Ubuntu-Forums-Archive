---
title: "ubuntu wireless connects only after windows"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by rrich1974 on 2013-06-11
hello!
i am experiencing a strange issue: 
i have a bcm4311 wireless card and i have this scenario: 
i have a network with two wireless acces points (only one ISP). both this networks are in range of the laptop. 
on windows (same machine, dell inspiron 1521), i can connect to both acces points witout any issue. but when it came to ubuntu, it only connects to the the access point that was used by windows when the windows was shut down. 

recap: 
my access points are named Tenda and Tenda-2
boot windows, connect to tenda, switch to ubuntu and can only connect to tenda
boot windows, connect to tenda_2, switch to ubuntu and can only connect to tenda_2.
windows works fine on both access points. 

if you need advanced info i will post the syslogs. this is happening on both 12.04 and 13.04. 

thanx in advance!

---

### Post by wyliecoyoteuk on 2013-06-11
Probably the firmware is set by windows, and Ubuntu can't change it.
Firmware for wifi cards is often only loaded at cold boot.
Restarting will not load it properly.
Try shutting down fully (power cycle) and  then boot into Ubuntu first.

---

### Post by rrich1974 on 2013-06-12
i tried shutting down an then power on the machine but no luck so far. 

after further investigation i found that if i shut down the WAN router and then power back on, gives me the possibility to connect to any of the two access points. but if i connect to one, i cant switch to the other one. i must power off/on the WAN router (broadcast router) again.

---

### Post by BazBear on 2013-06-12
This is an odd one, what brand and model routers are they?

---

### Post by rrich1974 on 2013-06-12
the WAN router (broadcast router) is an Edimax and the access points are Tenda

---

### Post by richardsdma on 2013-08-06
really strange issue, nobody? 
bump

---

