---
title: "apache 2 - download html file"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by luftadler on 2010-03-15
Hi 

I have this problem... 

I've reinstall the apache because of a starting problem  and now it give me to download HTML files.

It is not strange? :shock:
Any ideas?

Thanks,
Cristian

---

### Post by mikemelen on 2010-03-15
have you check all php modules are enabled? are you getting default page.

---

### Post by dokaspar on 2010-03-15
What exactly is the problem?

---

### Post by luftadler on 2010-03-15
When i browse **localhost** it give me to save an PHTML file 
```
jqMJ9ohf.phtml.part
```
In the root folder i have an **index.html** file

---

### Post by mikemelen on 2010-03-15
Have you installed libapache2-mod-php5. For installing please run below command

aptitude install php5 libapache2-mod-php5

and restart the apache

/etc/init.d/apache2 restart

---

### Post by luftadler on 2010-03-15
ya ... all installed and verified
but it was not a problem with php ...
anyway resolved by removing apache and all dependencies and reinstall all packages

thanks for replays
 Cristian
:P

---

### Post by varunkant on 2010-03-16
Is this possible to install apache in ubuntu 9.10 karmic-kola?
or is there any software so that i launch a web site which work on LAN.?

---

### Post by luftadler on 2010-03-16
Yes you can install apache on Ubuntu (9.10)

here are few tips

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

after that you must configure  apache to work on lan or intranet 
and you can access  your website trough your ip address

---

