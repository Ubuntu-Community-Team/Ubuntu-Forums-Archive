---
title: "can not establish network connection"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by shadheen on 2010-12-24
Hello,

I am using a pppoeconf and route del default does not work. 
after pnig [www.google.com](www.google.com) noting is happening.

---

### Post by shadheen on 2010-12-24
route -n

```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.75.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
X.Y.Z.W     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
X.Y.Z.W     192.168.75.1    255.255.255.255 UGH   0      0        0 eth0
192.168.75.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.75.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


```

---

### Post by dineshs on 2010-12-24
What does ```
cat /etc/network/interfaces
```say?
Which ubuntu version are you using?
Did you configure Network manager manually ?
Did you run ```
sudo pon dsl-provider
``` before trying ping google.com?

---

### Post by shadheen on 2010-12-25
> **dineshs said:**
> What does ```
cat /etc/network/interfaces
```



```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```


say?
Which ubuntu version are you using?
Did you configure Network manager manually ?
Did you run ```
sudo pon dsl-provider
``` before trying ping google.com?
ubuntu 10.10.

---

### Post by shadheen on 2010-12-25
Is there anyone who can help regarding this problem.

---

