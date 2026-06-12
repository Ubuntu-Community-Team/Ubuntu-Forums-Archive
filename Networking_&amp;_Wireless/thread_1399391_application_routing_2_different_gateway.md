---
title: "application routing 2 different gateway"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by charlie.a on 2010-02-05
Hello,
 
My Laptop is connected to 2 different network 
(Wireless "gateway 10.170.8.1" ;cable wired "gateway 192.168.1.1")
the gateway 192.168.1.1 is the default 
i want all application like firefox that connect via http and https port 80 and 443 to use the gateway  10.170.8.1)
else to use the default gateway

Thank you for your reply,
Charlie

---

### Post by Crafty Kisses on 2010-02-05
I'm not understanding you're question that well, but first can I see your kernel routing table? Open a terminal and run the following command:
```
route
```
Once you have ran route, copy and paste the results and post them back here at the forums. Now I'm not really understanding what you actually want to do with the Gateway, so you want to do something like this?
```
**192.168.1.44** -> Gateway = 192.168.1.2
**192.168.1.45** -> Gateway = 192.254.1.2
```
I'm not sure what you're asking, but tell me if that's right.

---

