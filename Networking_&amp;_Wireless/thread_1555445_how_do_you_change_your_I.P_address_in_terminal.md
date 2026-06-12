---
title: "how do you change your I.P address in terminal?"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by KEE on 2010-08-18
hi, 
I want to know how do I change the ip in terminal? please and thanks=)

---

### Post by nbkr on 2010-08-18
There are two commands. The older one:

```
sudo ifconfig <interfacename> <newip> <newnetmask>
```

The newer one is 

```
sudo ip addr add <newip>/<netmask> dev <interfacename>
```

---

