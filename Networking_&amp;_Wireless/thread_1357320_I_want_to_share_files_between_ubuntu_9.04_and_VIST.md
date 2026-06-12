---
title: "I want to share files between ubuntu 9.04 and VISTA (AP/Router)"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by lse123 on 2009-12-17
I want to share files between ubuntu 9.04(soon 9.10) and VISTA (AP/Router) or between ubuntu 9.04(soon 9.10) and XP (AP/Router) mainly Wirelessly well, what to do ? Try first with ethernet cable and after Wirelessly ? where in ubuntu I may see the Windows networked PC ? How start sharing files ?

---

### Post by Grenage on 2009-12-17
To graphically browse network Windows shares in Ubuntu, open Nautilus (the default file manager) and type into the address bar:

```
smb://windowsmachine/sharename
```


Or click on *network* in the left pane of Nautilus, and browse.

---

### Post by lse123 on 2009-12-19
where find linux ubuntu 9.04 share name ?

---

### Post by sanderj on 2009-12-19
> **lse123 said:**
> where find linux ubuntu 9.04 share name ?

By default, it's the name you see with "uname -a" (or "uname" alone).

And you should see it in Nautilus -> Network

---

