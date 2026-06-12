---
title: "Importance of moduli file"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by manyu_aditya on 2009-12-12
What is the importance of it. More importantly what if I delete the file. Will it get automatically recreated?

---

### Post by chili555 on 2009-12-12
May we assume you mean */etc/modules*? Its purpose is to load kernel modules that should be loaded at boot time. In a default file, only one module is listed: lp. I would not suggest removing it.

The file will not, as far as I am aware, get recreated automatically. If there is something going wrong, I believe it is better to amend it. 

If I am incorrect about the file you are referring to, please correct me.

What are you trying to accomplish? Maybe we can suggest another solution.

---

### Post by manyu_aditya on 2009-12-13
Sorry for not making it clearer. Actually I meant /etc/ssh/moduli

I read the man page but it's not clear what exactly it does. What happens if I delete it etc.

---

