---
title: "No Avidemux anymore since 16.04"
date: 2016-04-22
forum: Multimedia Software
---

### Post by Laui on 2016-04-22
There is no Avidemux anymore since 16.04 in the official Repositories, Why?

---

### Post by fabioepneves on 2016-04-23
Same problem here. Anyone?

---

### Post by Rob Sayer on 2016-04-24
I suspect it isn't sufficiently tested yet.  This sort of thing is not unusual with a new linux release.

---

### Post by mc4man on 2016-04-24
I remember seeing some attempts to build for 16.04 that failed (qt version), don't remember where though. 
I'd suspect getdeb has packages, don't know as have no use for getdeb
If you want to test a package for 16.04 I've put here, if it works ok great, if not let me know. If unsuitable i'll just delete the ppa  as myself not much time to explore, ect.
[https://launchpad.net/~mc3man/+archive/ubuntu/avidemux1](https://launchpad.net/~mc3man/+archive/ubuntu/avidemux1)

---

### Post by Laui on 2016-04-26
here [http://www.ubuntuupdates.org/package/getdeb_apps/xenial/apps/getdeb/avidemux2.6-qt](http://www.ubuntuupdates.org/package/getdeb_apps/xenial/apps/getdeb/avidemux2.6-qt) you can get a *avidemux2.6-qt_2.6.12-1~getdeb3~xenial_i386.deb* oder 64bit. But gdebi error message at install

[IMG]http://abload.de/img/2016-04-25-111807_571plsce.png[/IMG]

---

### Post by gedakc on 2016-05-16
Thank you mc4man for providing a PPA for avidemux on ubuntu 16.04.

I successfully installed avidemux on kubuntu 16.04 with the following commands:

> 
sudo apt-add-repository ppa:mc3man/avidemux1
sudo apt-get update
sudo apt-get install avidemux


I then successfully ran avidemux using the *K -> Multimedia -> Avidemux (Qt)* menu item.

---

### Post by antonio66 on 2016-05-17
Yes, it works, very well, thank you! :D

---

