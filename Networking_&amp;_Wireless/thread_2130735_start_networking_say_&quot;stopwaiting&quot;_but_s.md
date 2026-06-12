---
title: "start networking say &quot;stop/waiting&quot; but started, why?"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by comutt on 2013-03-30
I got the following message when running sudo /etc/init.d/networking start:

```

$ sudo /etc/init.d/networking start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting

```

So, I tried sudo start networking (after sudo /etc/init.d/networking stop) and got the following message:
```

$ sudo start networking
networking stop/waiting

```

It seems that the system say networking hasn't been started correctly, but checking the eth0 results it's wrong:
```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 08:00:27:62:08:36
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe62:836/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:76460581 (76.4 MB)  TX bytes:2170914 (2.1 MB)

```

Question: Why Ubuntu always say "stop/waiting" after either sudo /etc/init.d/networking start or sudo start networking?

Additional information as follows:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

```

---

### Post by steeldriver on 2013-03-30
In newer desktop editions, the interfaces are managed by the 'network-manager' service, not the 'networking' service

```
service network-manager status
```

---

### Post by comutt on 2013-03-30
> **steeldriver said:**
> In newer desktop editions, the interfaces are managed by the 'network-manager' service, not the 'networking' service

```
service network-manager status
```

I'd removed network-manager because I'm using CUI basically. (I think network-manager is for GUI, right?)

So, there isn't a way to see that the networking is correctly started with rc.d, service or upsart?

I came from CentOS world, and /etc/init.d/network restart shows their success/failure message with OK or NG.
In Ubuntu, what's operation is equivalent?

---

### Post by steeldriver on 2013-03-30
Hmm well I hadn't noticed that before but my 12.04.2 server box says the same:

```
$ service networking status
networking stop/waiting
$ 
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe86:ee0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45159 (45.1 KB)  TX bytes:16650 (16.6 KB)
          Interrupt:16 Memory:ee000000-ee020000 

$ service network-manager status
network-manager: unrecognized service

```

---

### Post by karnalta on 2013-04-12
I have the exact same "issue".

But I only noticed it because since today my Ssh service doesn't start with the server anymore. I don't know if it's link with that or if that networking problem was there since the fresh Ubuntu install.

---

