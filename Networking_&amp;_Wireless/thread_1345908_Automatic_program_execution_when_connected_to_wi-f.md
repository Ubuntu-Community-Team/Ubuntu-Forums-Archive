---
title: "Automatic program execution when connected to wi-fi"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by zatix on 2009-12-04
hello,

I would like to know how can I configure my gnome to make that when the wi-fi connects to a determinated hotspot then I want a program to be executed automaticaly.


I would like to do this because if for example I am at the university(fast network) I  want my bit torrent running the more time possible without having to open it each time.

Any idea?

Thanks!

---

### Post by puppywhacker on 2009-12-04
if you use the hand-configuration in /etc/networking/interfaces you can add an ifup script, that script could start-up your application, or even figure out on which network you're connected... you'll have to google/script the ifup yourself

---

