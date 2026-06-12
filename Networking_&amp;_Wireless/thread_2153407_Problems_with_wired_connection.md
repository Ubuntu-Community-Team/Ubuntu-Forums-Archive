---
title: "Problems with wired connection"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by tonitones on 2013-06-11
I just installed Lubuntu on Windows XP so im dual booting right now. I chose Lubuntu cause most people say its lightweight OS for old computers. I am also new to Ubuntu.

here is my prob:
 On windows XP the internet connection is fine and when I boot to Lubuntu, a "Wired Connection is disconnected" message keeps on showing on the upper right corner of the screen. I have no idea what is going on. Do I need to install a driver or something? or are there any configurations to be set? :(

---

### Post by Hadaka on 2013-06-11
Hi, please open a terminal...ctrl/alt/t
then copy and paste the following..
```
lspci -n | egrep '0200|0280'
```
post the results
thanks.

---

### Post by tonitones on 2013-06-11
Sorry for the late reply. I just got home from school. So yeah, imma go try that code now and when i get back I'll post the results.

Thanks for the reply btw. :)

---

### Post by tonitones on 2013-06-11
here is the result:
this line showed up after writing down the code,
02:03.0 0200: 10ec:8139 (rev 10)

so what does it mean? :o

---

