---
title: "create ftp"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by navaneethan on 2009-09-26
Hi we have the ftp site :[ftp://172.16.4.36](ftp://172.16.4.36) and we want to create the ftp like [ftp://172.16.**.**](ftp://172.16.**.**) for particular system ip(depends on)

how to make the ftp for the system which i want

---

### Post by shredder12 on 2009-09-26
can't you change your system IP ...
the ftp address will change automatically...

---

### Post by navaneethan on 2009-09-26
I need to set a fresh ftp for my ip,i ve known my ip

---

### Post by shredder12 on 2009-09-26
i am a little confused..
are you saying you already have a ftp set up on your machine..???
and what do you really want to do??

plz.. clarify.. i didn't understand ur problem..

---

### Post by navaneethan on 2009-09-27
> **shredder12 said:**
> i am a little confused..
are you saying you already have a ftp set up on your machine..???
and what do you really want to do??

plz.. clarify.. i didn't understand ur problem..

just i need to create a fresh ftp to share files from LAN in linux

---

### Post by shredder12 on 2009-09-27
Oh.. if you only want to create a new ftp server then I may suggest you my personal favourite vsftpd..
For its installation jst enter the following command..
```
sudo apt-get install vsftpd
```
This will install the vsftp server on your machine..
for more details about it take a look here..

[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

---

