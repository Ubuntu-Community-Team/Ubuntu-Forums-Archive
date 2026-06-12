---
title: "&quot;Network&quot; Option has disappeared in Thunar after upgrade"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by atomicspin on 2012-12-25
I've upgraded to 12.10 on 3 of my machines and 2 of them no longer have the "Network" option in Thunar.  

They were all working fine in 12.04.  Anyone know what I may have messed up?

---

### Post by Toz on 2012-12-27
Do you have the **gvfs-backends** package installed?

---

### Post by atomicspin on 2013-01-04
Bump.

---

### Post by Toz on 2013-01-04
So, do you have **gvfs-backends** installed? Search for it in the software centre and see what it says, or from a terminal window:
```
apt-cache policy gvfs-backends
```

---

### Post by atomicspin on 2013-01-04
> **Toz said:**
> So, do you have **gvfs-backends** installed? Search for it in the software centre and see what it says, or from a terminal window:
```
apt-cache policy gvfs-backends
```

I do.  I've also done a complete removal and re-installation of it.  

Thanks for replying.

---

### Post by Toz on 2013-01-04
Which gvfs packages do you have installed:
```
dpkg -l | grep gvfs
```
...maybe another is missing.

---

