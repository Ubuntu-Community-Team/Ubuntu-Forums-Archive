---
title: "Wireless Extensions"
date: 2006-04-03
forum: Networking &amp; Wireless
---

### Post by wile_e8 on 2006-04-03
Hello, I've been in the beginner forum getting help for my wireless problems in [thread=153373]this thread[/thread], but I was getting no response so I thought I'd try here.  After few questions and answers, I was told that to run ```
iwconfig --version
``` and it came back with this response
```

allan@wileylap:~$ iwconfig --version
iwconfig  Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v18.

Kernel    Currently compiled with Wireless Extension v17.

eth1      Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v17.

```

How would I update the wireless extensions as recommended by iwconfig?

---

### Post by hw-tph on 2006-04-03
You will need to get a newer kernel, or patch your current one with the wireless extensions v18 patch and then rebuild it.

This would be needed if you have problems relating to the version of wireless extensions that you use. However, most problems with wireless networking have nothing to do with this, so it is only a warning - you don't *have* to upgrade.


Håkan

---

