---
title: "static ip  address permission"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by benh13 on 2009-07-08
when trying to edit /etc/network/ interfaces to gain a static ip, i can't get permission to save the file? how can i get permission?

---

### Post by renzokuken on 2009-07-08
you need to open the file using sudo/gksudo as a standard user will not have permission to edit it......try opening a terminal then using the following command

```
gksudo gedit /etc/network/interfaces
```

---

### Post by benh13 on 2009-07-08
thanks that helped me gain permission

---

