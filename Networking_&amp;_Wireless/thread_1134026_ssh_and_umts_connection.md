---
title: "ssh and umts connection"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by ShanshanZg on 2009-04-23
Hi Everyone, 
I have two computers, a desktop and a laptop, both installed Ubuntu 8.10 64 bit. Desktop connects to the internet via local Ethernet and laptop via UMTS by using Sierra Compass 885. 
Laptop can ssh desktop but the other way around, desktop cannot ssh laptop. 
Laptop's Ip address from /sbin/ifconfig section ppp0 is different from the one displayed by whatismyip. Neither of them can be sshed by the desktop. 

What should I do to make laptop reachable by ssh from another computer?

Thank you,
Shanshan

---

### Post by Peter09 on 2009-04-23
You need to install openssh-server on a machine before you can ssh into it.

```
sudo apt-get install openssh-server
```

---

### Post by ShanshanZg on 2009-04-23
openssh-server is already installed. This is not the reason, because I am able to ssh the laptop from the desktop, if the laptop is connected to internet via WLAN or Ethernet. It seems to me in case of connection via UMTS, the laptop's ip address I got from /sbin/ifconfig and whatismyip are not its real the ip. The Sierra Compass 885 must have done something in-between. 

Anyone knows how to deal with this problem?
Thanks,
Shanshan

---

### Post by ShanshanZg on 2009-04-24
Please please help...
Anyone have an idea?
Shanshan

---

### Post by Vishal Agarwal on 2009-04-24
you need to forward the ssh from your laptop to some connecting mediator IP. Laptop is not getting the direct Ip, that's why it can not be accessed from desktop. the desktop IP is visible to laptop, so that the laptop is able to connect to desktop.

---

