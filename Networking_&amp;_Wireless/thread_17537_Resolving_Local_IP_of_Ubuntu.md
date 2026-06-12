---
title: "Resolving Local IP of Ubuntu"
date: 2005-03-01
forum: Networking &amp; Wireless
---

### Post by shrekkie on 2005-03-01
Hi there, 
              I am new to linux/unix so please bear with me. I installed ubuntu using VMware and I am using it as I was recommended to install it by my lecturer as I am doing a programming paper. Ubuntu configured my network automatically during installation using DHCP, but I can't find the local IP address of ubuntu so I can allow this IP in my windows firewall so I can access windows shares through the workgroup. I can access internet through the network, but I can't access any shares from windows. VMware uses bridged networking by the way, if that helps. Is there any way for me to find the local ip of ubuntu? something like 192.168.X.X i guess

---

### Post by Juergen on 2005-03-01
Open a xterm and type ```
ifconfig -a
```then look what's displayed for 'eth0' (most probably)
And maybe take the time and type 'man ifconfig' for additional info.

---

### Post by shrekkie on 2005-03-03
thanx a lot for that reply, although I still can't access my shared folders from windows yet. I must be doing something wrong :(

---

### Post by byourg on 2005-03-03
In the network properties for you lan card select 'general' there should be a box to enter your window$ network workgroup for Samba.

---

