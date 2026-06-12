---
title: "how to connect to rlogind port 513 using ssh"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by jao_madn on 2011-07-02
Hi 

Gud day,

Im facing this problem on how to connect to solaris 8 service rlogind listening to port 513 using ssh. I had no luck in establishing a connection using ssh in the rlogind. is there a way that i something missed or dont know know on how to accomplished my objective. or theres no posiblity to connect the ssh in the rlogin service and need to install a rsh package in my ubuntu linux box. Im hoping there some command in ssh that is missed and hope someone can share it.

---

### Post by stlu on 2013-04-08
For anyone asking the same question (since this ranks high in google), it is important to know that the commands /usr/bin/rlogin and /usr/bin/rsh in current versions of Ubuntu are links to **/etc/alternatives/** which link to ssh in a default install.  Therefore, to use these programs, you will need to install them.

Note that ssh will not connect to an rlogind service by default even if you specify connecting to port 513.

(sorry for necro)

---

### Post by wildmanne39 on 2013-04-08
Thanks for sharing, old thread closed!

---

