---
title: "Wireless connecting-No internet"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by sadanandan on 2010-04-14
I have installed a wireless card in my Ubuntu 9.04 System. When I start Firefox, it keep searching for a while and it cannot connect to the internet.
I need the help of someone knowledgeable to solve this problem. I have attached screen shots of network connections.
Forgot to add an important point- when I type the address of the router in the browser address window, it cannot access the router.

---

### Post by Iowan on 2010-04-14
Having eth0 and wlan1 in the same subnet may be causing problems for routing. Try disabling the wired interface. If both are defined in Network Manager, you can uncheck "Connect Automatically". No guarantees, but worth a try...

---

### Post by sadanandan on 2010-04-15
Thank you Iowan. Your solution did work. By disabling the wired network I am able to connect to the internet. Thank you once again for your help

---

