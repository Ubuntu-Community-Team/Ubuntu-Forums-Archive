---
title: "Estabish connection"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by coolmadmax on 2009-04-04
I have crossover LAN  and i put IP address manually to both systems 192.168.0.1 and 192.168.0.2. when i try to add network folder Webdev,ftp,ssh or Microsoft Windows with my ubuntu system always getting message couldn't find host or server. Why i have this problem that could not establish connections ?

---

### Post by cariboo on 2009-04-04
Add aliases for both machines in your /etc/hosts file eg:

```
192.168.0.1    computer1
182.168.0.2    computer2
```

you can substitute whatever names you want to use.

---

