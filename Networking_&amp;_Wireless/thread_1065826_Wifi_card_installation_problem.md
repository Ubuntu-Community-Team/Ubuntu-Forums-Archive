---
title: "Wifi card installation problem"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by bud69500 on 2009-02-10
Hi everyone,

I have just installed a wifi card (from the brand Dynex) in my desktop computer on a PCI port. My problem is that if I launch ifconfig I only see eth0 which is my cable network connection. However, if I launch iwconfig I clearly see something called wlan0 which seems to be my wifi card. I tried to configure manually the connection with iwconfig and then launch dhclient but my computer cannot get its IP on the network.
Does anybody know why my card does not appear with ifconfig? What could I try to change that?
Thanks.

---

### Post by azr on 2009-02-10
I don't know why the two commands appear to contradict each other - but have you loaded the driver for your card with

```
modprobe *driver* ?
```

---

### Post by bud69500 on 2009-02-11
I actually reinstalled ubuntu 8.10 and still got the same problem. I tried to do what you told me but I did not know what was the name of the driver I was suppose to load.
Finally I installed ndiswrapper and succeeded to make it works.
Thanks for you help though.

---

