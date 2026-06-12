---
title: "Can't turn on wifi (Atheros  AR5007EG)"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by cyrusvn on 2008-12-12
Hi everybody,

I got some problem with my wireless connection.

Recently I installed Ubuntu 8.10 and I can't seem to get my wireless working.

I have installed ndiswrapper and ndisgtk, ubuntu recognised the device but there is no way I can turn on the wifi.

I did

```
sudo lshw -c network
```

and saw this:

```
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:dd:1d:8c:dd:ef
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

So what's wrong with it?

My network adapter is AR5007EG and my laptop is Asus Pro50N.

---

### Post by iponeverything on 2008-12-12
Is there a FN key combo for it?

---

### Post by cyrusvn on 2008-12-12
yes, it's Fn+F2 but it doesn't work.

---

### Post by superprash2003 on 2008-12-12
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

