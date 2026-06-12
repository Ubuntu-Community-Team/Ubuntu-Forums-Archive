---
title: "Internet sharing among computers"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-08-20
I am trying to share Internet with another computer. I was able to do that by establishing a dhcp server and firestarter but I want the other computer to be on the same subnet as the main computer. Is this possible??

---

### Post by Iowan on 2009-08-20
The interfaces over which the two machines communicate would seem to require that they (the interfaces) be in the same subnet.

---

### Post by shredder12 on 2009-08-21
Yes, I searched for it and found out that some network interface bridging must be done to make it work. But i couldn't find any good documentation for this purpose..
Could anyone help me with that??

---

### Post by jamest09 on 2009-08-21
Point the other computer at the main computer with a default route, the enable ip forwarding on the main computer.

Simples

---

