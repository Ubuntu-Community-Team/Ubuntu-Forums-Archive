---
title: "eth0 not visible in network connections"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by wschulte on 2011-01-24
Since I installed ubuntu 10.04 I dont see my eth0 card in System->Preferences->Network _connections. Everything works fine but it puzzles me. In ifconfig iI just see the eth0, networking seems to be working fine, but it keeps puzzling me. Adding theinterface is no solution: add it and it doesnt show again -:(.

Anybody an idea ?

Greetz, Willy.

---

### Post by Iowan on 2011-01-24
Was interface (eth0) configured via Network Manager, or */etc/network/interfaces*?

---

### Post by wschulte on 2011-01-24
Well it wasnt configured at all .. ic. it was just there after installation. .. but not in the network connections though ..

---

### Post by yoyoq on 2011-04-15
same problem here. 10.04.2, i started with dhcp.
then when the network guys gave me a fixed address
i editted /etc/network/interfaces 
took a few reboots but now the network looks ok,
i am hosting a websirte that looks ok and i can see
other webpages ok, but it is not listed in 
"Network Connections"

---

### Post by amsweitzer on 2011-04-15
i installed clonezilla server erred in the install when it configed my network connetion I have uninstalled drbl and clonezilla used mint on other filesystem to copy my network conf then went back to ubuntu and configed to what was in mint it still will not work it shows the eth in loop when I do a ifconf but when I do an ehernet restart it shows device eth0 not found is there an auto detect/ auto config that i can install like on some live distros

---

