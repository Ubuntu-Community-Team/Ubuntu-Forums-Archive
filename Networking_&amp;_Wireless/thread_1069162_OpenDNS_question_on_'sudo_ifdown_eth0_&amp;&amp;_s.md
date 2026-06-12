---
title: "OpenDNS question on 'sudo ifdown eth0 &amp;&amp; sudo ifup eth0'"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-13
I have followed [this guide]("https://www.opendns.com/start/ubuntu.php") to setup OpenDNS. I notice at the end it says 'sudo ifdown eth0 && sudo ifup eth0'. This is for wired, yes? I am connected wirelessly so 'sudo ifdown eth0 && sudo ifup eth0' is not appropriate. Would right clicking on NetworkManager Applet 0.7.0 and unticking 'Enable Wireless' and then ticking 'Enable Wireless' be the wireless equivalent for 'sudo ifdown eth0 && sudo ifup eth0'?

---

### Post by cariboo on 2009-02-13
Just open a Applications-->Accessories-->Terminal and type:

```
sudo /etc/init.d/retworking restart
```

it does the same thing.

Jim

---

### Post by Rytron on 2009-02-13
> **cariboo907 said:**
> Just open a Applications-->Accessories-->Terminal and type:

```
sudo /etc/init.d/retworking restart
```

it does the same thing.

Jim

Thank you Jim. Just a minor spelling correction:

```
sudo /etc/init.d/networking restart
```

Cheers.

---

