---
title: "2Wireless"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by intel 4004 on 2010-10-24
So I have win 7 and Ubuntu in my laptop, in win 7, I can use wireless connection, but in Ubuntu, I can't. Is it the driver problem? or just the router is not compatible with it? If its the driver problem, where I can get the software?

---

### Post by grahammechanical on 2010-10-24
Open a terminal and type

```
nm-tool
```

It should give you a list of your network devices. Look for wlan0. It should list the type, driver and if it is connected or not. If it shows a list of wireless access points then wireless is working on your machine. It is not connecting for some other reason.

Regards

---

### Post by intel 4004 on 2012-03-29
Ok problem solved, need to post here so if someone comes over, maybe this might help

[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

---

