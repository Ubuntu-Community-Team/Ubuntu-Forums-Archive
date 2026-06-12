---
title: "Network Notification"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by Frogs Hair on 2012-12-26
I have been using Ubuntu on non-shared lan since my first installation. Last spring we switched from DSL to Cable and I have been seeing the notification below ever since. I located a fix for this problem but it is outdated and no-longer works. I was wondering why this appears with Cable only ?

---

### Post by Frogs Hair on 2012-12-28
Just bumping :o Has anyone even seen this notification before with Time Warner Cable internet ?

---

### Post by steeldriver on 2012-12-28
I think it's a problem with the ISP's DNS servers (incorrectly, afaik) attempting to resolve .local

What fix did you use before? you could try changing your DNS settings to use Google or OpenDNS

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362)

---

### Post by Frogs Hair on 2012-12-28
Thanks , I have looked into open DNS. Below was the fix I tried and the change failed to save even as root.   

```
simply modify your /etc/avahi/avahi-daemon.conf with the following entry:

domain-name=.alocal
```

> Avahi will simply use the domain .alocal to do its magic.

---

### Post by Frogs Hair on 2013-04-27
The problem disappeared with a clean installation of 13.04 . :confused:

---

### Post by Frogs Hair on 2013-08-19
The problem did come back and was finally solved by adding a new  router  not provided by TWC .

---

