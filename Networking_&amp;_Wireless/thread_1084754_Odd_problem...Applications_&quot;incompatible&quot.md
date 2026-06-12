---
title: "Odd problem...Applications &quot;incompatible&quot; with the Internet"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by FrikkieLinux on 2009-03-02
All my application work while not connected to the internet. When I do connect to the internet (wired connection -> hub -> router -> broadband) all applications will not open. Even simple applications such as terminal attempt to open but don't.

I'm running Ubuntu 8.10.

Any ideas?
Thanks

---

### Post by chili555 on 2009-03-02
May we please see the result of the following terminal command?```
cat /etc/hosts
```It may have nothing to do with your problem, or it may be corrupted. Next, please do:```
top
```Leave it open and running as you surf the internet. When you try to open a terminal, are there any applications that are using 90%++ of your CPU cycles?

---

