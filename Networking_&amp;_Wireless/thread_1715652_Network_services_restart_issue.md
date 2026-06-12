---
title: "Network services restart issue"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by testacc753 on 2011-03-27
Whenever i restart the network services i get the following error...

prasanth@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for prasanth: 
 * Reconfiguring network interfaces...                                                    Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
                                                                                   [ OK ]

And some of the websites are also not getting opened...

---

### Post by Joel.S123 on 2011-03-27
The output of the following command would be helpful:
```
ifconfig
```

---

