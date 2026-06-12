---
title: "Configuring two ethernet cards...on Ubuntu Server."
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by akshay.sulakhe on 2009-12-14
Hello friends,
              Let me walk u through the scenario. Its Dell Poweredge 1800 server. It has two ethernet cards(eth0,eth1). There is one switch and a router. An input leased line is given to the switch. The output of switch is given as input to router. So with router we have a internal private address. With switch we can have a public address. They are hosting a site anywayz. Also eth0 is connected to router,which gives the internal address and eth1 is directly connected to switch. We configured /etc/network/interfaces. It is only taking the internal address and not going online via eth1. What should we do???

---

### Post by shairozan on 2009-12-14
When I hear leased line, I generally think of T1 or another serial connection. Those generally run into a T1 controller on a router or some other device that is capable of performing encapsulation controls. 

Could you please post your /etc/network/interfaces file? Also, have you tried to force eth1 up via 

```
sudo eth1 up

```

---

### Post by Iowan on 2009-12-14
As mentioned, the file will help...
How is eth1 getting it's address?

---

