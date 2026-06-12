---
title: "Can't connect"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by bobp365 on 2010-02-17
I had no trouble installing Ubuntu server  on a virtual server running windows server 2003 r64.
 
The problem is that the Ubuntu server will not see my network. It keeps creating a loopback network device, and will not configure no matter what settings I use.
 
Can anyone help?
 
Thanks,
 
bobp

---

### Post by Iowan on 2010-02-17
Loopback is required for the machine. You should have others as well - post results of **ifconfig -a**. If no other interfaces appear, also post results of **sudo lshw -C network**

---

