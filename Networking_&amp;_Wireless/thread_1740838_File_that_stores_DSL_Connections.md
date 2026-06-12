---
title: "File that stores DSL Connections"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by sarbaraj101 on 2011-04-27
Hello,

I am thinking of performing a fresh ubuntu install, but I have a LOT of DSL connections created in my laptop (10.10, created through the NetworkManager applet 0.8.1). Is there any file that stores the connection information, and if there is one, where is it?

Thanks
- Sarba

---

### Post by sarbaraj101 on 2011-04-28
anyone??? <<bump>>

---

### Post by dineshs on 2011-04-29
Run```
gksudo nautilus /etc/NetworkManager/system-connections
```
You will have seperate files for each DSL connection, ethernet....

---

