---
title: "sudo ifconfig eth0 mtu 1400"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by bogart_2003 on 2009-09-10
hello guys! finally got my internet connection working today. however, i have a bit of a problem. sees like the only way for me to browse properly is to input 
```
sudo ifconfig eth0 mtu 1400
``` 
everytime ubuntu boots. is there something i can do so that i wont have to do this every single time? thanks!

---

### Post by karthick87 on 2009-09-10
Goto "sudo gedit /etc/network/interfaces" add mtu 1400 next to the line iface eth0..Hope that works

---

### Post by bogart_2003 on 2009-09-10
thanks dude! but before i do that, how do i back up the file that i'm about to edit? so i dont mess things up. thanks again!

---

### Post by Iowan on 2009-09-10
If you set up the connection via Network Manager, you should be able to edit the connection (auto eth0?) and change MTU.

Otherwise, to make backup copy:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

Also, if you prefer [graphical]("http://www.psychocats.net/ubuntu/graphicalsudo") editor (**gedit**), use: ```
gksudo gedit /etc/network/interfaces
```

---

