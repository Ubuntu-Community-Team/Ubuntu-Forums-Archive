---
title: "need simple help with networking please NOOB"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by paleo on 2009-05-19
I have wireles network that shares windows files fine through SMB though very slow I want to use a wired connection through my eth0 port I set it up staticly I think I did it right **_sudo ifconfig eth0 10.0.0.4 mask 255.0.0.0 up**_ but I cant ping my windows box running vista I am running ver 9.04 gnome using a crossover cable I can't use the ports on the router because in a different room. Please help me.

---

### Post by dmizer on 2009-05-19
I assume the Vista box has two ethernet cards? If so, open a command prompt (run as administrator) on the Vista box and post the output of:
```
ipconfig /all
```

---

### Post by Iowan on 2009-05-19
Check your manual configuration with **ifconfig -a**.  Unless I misread the **man** page, that should read **_net_mask**...

---

### Post by superprash2003 on 2009-05-20
setup static ip using network manager , ensure both windows and ubuntu has an ip.. you can do that by posting the output of ipconfig and ifconfig from windows and ubuntu respectively

---

