---
title: "problem in firestarter firewall"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by poricoder on 2010-09-26
hi all .
i connect to internet with the connection(with Name : DSL Connection 1) that made by myself .
now i wanna use the firestarter but i have a problem .
this is my problem :
[IMG]http://irupload.ir/images/t2kkj9buuk29m9mxidw.png[/IMG]
help me .

---

### Post by sikander3786 on 2010-09-26
Are you sure your connection is live? Post the output of these commands.

```
ifconfig
```

```
ifconfig -a
```

---

### Post by perspectoff on 2010-09-26
And if not live, try restarting the networking once:

 sudo /etc/init.d/networking restart

And, of course, are you actually using eth0 (which is wired) or are you using wlan0 (wireless)? If using wlan0, you have to set Firestarter to use it, naturally.

---

### Post by poricoder on 2010-09-27
> **sikander3786 said:**
> Are you sure your connection is live? Post the output of these commands.

```
ifconfig
``````
ifconfig -a
```

oh yeah  .
i connected with ppp0 but use the eth0 in firestarter .
my problem solved . tanx all:P

---

### Post by poricoder on 2010-09-27
how can i block a site in firestarter with his name not IP address .??
for example when i want  open firefox and enter [www.google.com](www.google.com) in URL ,this site to be block for me .
help me .

---

### Post by Sef on 2010-09-27
[Firestarter]("https://help.ubuntu.com/community/Firestarter") is not actively maintained or being developed, so it cannot be guaranteed to be secure according the the community docs.

[Other firewalls]("https://help.ubuntu.com/community/Firewall").

---

