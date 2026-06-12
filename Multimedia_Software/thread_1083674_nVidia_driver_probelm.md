---
title: "nVidia driver probelm"
date: 2009-03-01
forum: Multimedia Software
---

### Post by newbieMD on 2009-03-01
hi everyone:

i am new to ubuntu...and am trying to get nVidia acceleration driver to work for me...but keeps on getting to the authentication screen and enters my password but unable to download or install.  do you have any suggestions?  I am running a dual boot of xp pro and ubuntu 8.1 on dell M1210.  thanks in advance.

newbie.

---

### Post by avrilrox on 2009-03-01
> **newbieMD said:**
> hi everyone:

i am new to ubuntu...and am trying to get nVidia acceleration driver to work for me...but keeps on getting to the authentication screen and enters my password but unable to download or install.  do you have any suggestions?  I am running a dual boot of xp pro and ubuntu 8.1 on dell M1210.  thanks in advance.

newbie.

This happened to me some time ago. I can't remember how to fix it.

Suggestions:

1) **Make sure you have a working internet connection.**
It needs to download the drivers from the internet, so you obviously need an internet connection.

2) Run **sudo apt-get update** in a console.
This will update the list of packages. If this works, it should download some stuff from the internet.

3) Make sure you're entering the correct credentials
If you're not logging in successfully, you will be prompted for username and password again.

4) If that doesn't seem to help, reboot and try again.
After installing packages, rebooting is not a bad idea.

---

### Post by norwoods on 2009-03-01
try the repository:
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

