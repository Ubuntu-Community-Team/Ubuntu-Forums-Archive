---
title: "network card not detected"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by FiskFisk33 on 2009-04-22
So i just installed ubuntu server 8.10 and it cant find the network card at all.
(no eth0, just the lo)
its a deltaco pci 10/100/1000 nic.
I need help

---

### Post by pytrisss on 2009-04-22
What about lspci or lsusb? Any signs of the NIC in the output of these commands?

---

### Post by Peter09 on 2009-04-22
Where i toy looking, these days /etc/networks/interfaces will not show all the active interfaces any more.

---

### Post by sahabcse on 2009-04-22
hi

Paste the o/p of #lspci and #dmesg

---

### Post by FiskFisk33 on 2009-04-22
lspci (the line i guess is the important one that is ^^):
```
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

from dmesg i get a huge amount of stuff i cant make any sense of, i cant even view it all by paging up.

---

### Post by Peter09 on 2009-04-23
Can you post the output of 

```
ifconfig
```

---

### Post by sahabcse on 2009-04-23
#sudo ifup eth0

---

### Post by pytrisss on 2009-04-23
> **sahabcse said:**
> #sudo ifup eth0

I dont think this will work if eth0 is not mentioned in /etc/network/interfaces

---

### Post by sahabcse on 2009-04-23
Try to add ip details /etc/network/interfaces and let us check the status

#sudo ifconfig eth0 xxx.xxx.xxx.xx netmask 255.255.255.0 up

---

