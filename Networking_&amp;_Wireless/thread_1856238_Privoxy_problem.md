---
title: "Privoxy problem"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by number777 on 2011-10-07
Good evening I'm new to this forum. I have a problem with setting privoxy. The problem is that I cant make changes into privoxy config, I have tried to make changes trough terminal with sudo vi /home/myuser/etc/privoxy/config, but i cant write to that file. Can somebody help please:)?

---

### Post by wildmanne39 on 2011-10-07
Hi, welcome to the forum! try using ```
gksudo gedit /home/myuser/etc/privoxy/config
```
Thank you

---

### Post by number777 on 2011-10-07
thats amazing! thank you very much finally I can write to that file.:D

---

### Post by wildmanne39 on 2011-10-07
Hi, your welcome! remember always use gksu or gksudo when opening a graphical application so root does not try to own it that will cause all kinds of problems,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

