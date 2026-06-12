---
title: "Address change"
date: 2012-08-18
forum: Networking &amp; Wireless
---

### Post by chuckrp on 2012-08-18
I have posted some issues that I am having with connecting a Myth and Win 7 computers. The Myth computer is wireless and the Win 7 is connected to the router via ethernet. I originally solved the problems with connecting the 2. I entered IFCON to obtain the address of the Myth computer. After a reboot of both machines, I could not connect. The Myth could see the Win 7 but the Win 7 could not see the Myth. I am trying to transfer videos from the Myth to the Win 7 so they could be converted to AVI files. I eventually found that the address of the Myth computer changed after the reboot. It went from xxx.xx.x.101 to xxx.xx.x.102 Is this normal for the address to change? How can I make it stay the same?
Thanks for any help.

---

### Post by lisati on 2012-08-18
There are different ways of coping, each of which has its own merits. My preference is to use the router to assign or reserve a static IP address to each machine.

---

### Post by Iowan on 2012-08-19
If the (Myth) machine is set for DHCP, then it might get a different address each time it reboots. You can assign it a static address (outside the DHCP range - but still within the subnet), or use the aforementioned static lease method.  I (also) prefer to let the DHCP server (router) manage IP addresses. Others might consider a DHCP server overly complicated for a small network.

---

