---
title: "SIOCADDRT: No such process ,, unable to bring up eth0"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-03-30
Believe   me people i have searched a lot before putting up this question here.. but i didn't get the solution..
I have installed hardy desktop edition (8.04.1) on a system. 
The system uses static ip addresses to connect to internet.. but when i did that.. and restart the system. i got the following error..
```
sudo /etc/init.d/networking restart
Reconfiguring network interfaces
SIOCADDRT: no such process
unable to bring up eth0
```

i have tried ```
ifup -a 
``` and got the same error..
any solutions..???

---

### Post by Iowan on 2009-03-30
Post results of **ifconfig -a** and contents of */etc/network/interfaces*.

---

