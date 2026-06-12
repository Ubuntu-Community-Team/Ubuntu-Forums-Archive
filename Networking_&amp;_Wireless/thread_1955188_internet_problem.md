---
title: "internet problem"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by greathtg on 2012-04-09
i have ubuntu 11.10 alongside windows 7 on my pc. whenever i log into ubuntu and try to connect to internet, it doesn't connect whereas i dont have any problem when i use windows. my isp hasn't given me any permanent ip address. i have selected "connect automatically" option. please help.

---

### Post by roelforg on 2012-04-09
> **greathtg said:**
> i have ubuntu 11.10 alongside windows 7 on my pc. whenever i log into ubuntu and try to connect to internet, it doesn't connect whereas i dont have any problem when i use windows. my isp hasn't given me any permanent ip address. i have selected "connect automatically" option. please help.
How did you install?
Wubi or seperate partition or seperate hd?
Laptop or desktop?
And please post the output of (note: the lshw can take time, just let it run until the prompt comes back):
```

sudo lshw -C network
sudo ifconfig -a
sudo lspci
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf

```

---

### Post by Bucky Ball on 2012-04-09
Have you clicked on the network icon and if so can you see your network there? If a fresh install, have you gotten online with a cable, gotten updates and then checked 'Additional Drivers' for drivers/firmware for your card?

Incidentally, those commands in the last post one at a time ... ;)

---

