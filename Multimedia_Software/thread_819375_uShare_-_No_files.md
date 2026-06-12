---
title: "uShare - No files"
date: 2008-06-05
forum: Multimedia Software
---

### Post by neilneil2000 on 2008-06-05
Hi, 

I had ushare running and everything was fine, however I since changed the ethernet adapter and a lot of network stuff stopped working so I uninstalled and reinstalled ushare.

I can see the Server on windows machines and on my Xbox but everything says there are no files within the shared folder.  Ihave tried many different folders and can't get round it!

I am running Hardy Heron 8.04

---

### Post by neilneil2000 on 2008-06-10
Anyone?

---

### Post by TJ-Tigger on 2008-06-16
does your new adapter show as eth0?  I was thinking that in the config file there was an entry for which interface ushare used.

ifconfig -a to look at your interfaces

and the config file is in /etc/ushare.conf.  There may be a network interface in the init file as well. /etc/init.d/ushare.

---

### Post by neilneil2000 on 2008-06-16
Thanks for the reply.

My new adapter is eth0 as I modified these files

```
/etc/udev/rules.d/70-persistent-net.rules
/etc/network/interfaces
```

I can see the shares but there is nothing in them.

Very Annoying

---

