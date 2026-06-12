---
title: "Sharing connection...."
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by msutton73 on 2010-07-27
When I installed 10.04 on one computer I was able to select the share with other computers in the network config and the internet worked on the ubuntu box and the win XP box found it and was able to use it. Now the XP box got infected with some viruses and so I put ubuntu on it also. But the internet connection doesn't work on what used to be the XP box anymore. How do I configure the 2 ubuntu boxes to share the internet connection.
Box 1 = eth1 internet
        eth0 ethernet card to box 2 connected with crossover cable.

Box 2 = eth1 connects to box 1

Thanks
Marc

---

### Post by Iowan on 2010-07-27
Clarification: 
The first Ubuntu box has been successfully sharing an Internet connection?
It's only the second Ubuntu box that's having problems with the share? How did you "share with other computers in the network config"?

---

### Post by msutton73 on 2010-07-28
Yes the first box was sharing with a windows XP box just fine.
Yes the second ubuntu box is what will not connect.
In the network settings on the computer that is sharing the internet connection. On eth0 ipv4 settings "shared to other computers".

---

### Post by Iowan on 2010-07-28
Connection setup? 
How does the second machine get IP address - DHCP or static? (DHCP would suggest that you have a DHCP server on first machine.) IF static - are the two machines in the same subnet? Can they ping each other?

---

