---
title: "How to see localhost site in the other networked computers"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by hannah187 on 2011-08-08
Hi,
I have developed a site in localhost in my laptop.
Here are the specs:
Ubuntu 11.04, Joomla! 1.7, Db Ver: 5.1.54-1ubuntu4, PHP Ver: 5.3.5, Web Server Apache/2.2.17 

This laptop is connected to a wi-fi network.
Task: I like to see this local site from my laptop to other desktop computers in the same network.
I understand that I need to do some changes in /etc/hosts

Please advice what changes I need to do to be able to see my localhost site in the network.

Regards

---

### Post by wojox on 2011-08-08
Can't you connect with the local adress? Use 

```
ifconfig
```

It will show you. Mine is

```
inet addr 192.168.0.36
```

---

### Post by hannah187 on 2011-08-08
> **wojox said:**
> Can't you connect with the local adress? Use 

```
ifconfig
```

It will show you. Mine is

```
inet addr 192.168.0.36
```

Legend.. that did it..

Much love

---

