---
title: "How do you open a port?"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by bobmatino17 on 2009-04-10
Well, I was recently trying to do some gaming, but for it to network properly it needs port 2092 open. How would I do that?

---

### Post by Kulgan on 2009-04-10
Ports in ubuntu are, as far as I know, only "closed" until something is actually listening to that port. You can list this with 

```
netstat -plntu
```

While the application is running. If port 2092 is listed, it should be "open". 
Is this LAN or online gaming you're doing?

Otherwise, have a look at the docs for iptables: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by superprash2003 on 2009-04-11
thats right.. you really dont have to do anything to open a port in ubuntu.. if there is an application listening to a port in ubuntu then ubuntu would automatically open that port..

---

