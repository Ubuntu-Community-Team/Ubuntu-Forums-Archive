---
title: "Problem with wifi network"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by SenK on 2012-07-20
Hi,
Right now I am using Ubuntu 12.04 alongside with windows operating  system. I have installed this Ubuntu with Wubi. Right now I am facing  problem with wifi network in my apartment. The respective wifi network  can be connected very easily. But I am unable to access internet  connection. All the time Mozzila shows 'Server not fount'. But  interestingly I can connect to university wifi network and access the  internet. So what is the problem? How can I get rid of this problem.  I  am quite worried that frequently I need to travel many places. So wifi  connection with proper internet is required. 
Please help me. I am very new with Ubuntu OS.

---

### Post by nothingspecial on 2012-07-21
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2012-07-21
> **SenK said:**
> The respective wifi network  can be connected very easily. But I am unable to access internet  connection. All the time Mozzila shows 'Server not fount'.
I may not be available to reply anytime soon, but those who can may need the following info:
```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
ping -c4 google.com
```

Enter the above commands in the terminal and post back the results (wrap the outputs in 'Code' tags as I did above).

---

