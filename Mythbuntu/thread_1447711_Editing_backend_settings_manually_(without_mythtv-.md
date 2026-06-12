---
title: "Editing backend settings manually? (without mythtv-setup)"
date: 2010-04-05
forum: Mythbuntu
---

### Post by OpenHeadWound on 2010-04-05
Hi Folks,
 
Just wondered if there is a script based method or SSH friendly way to edit backend settings.  Installing on an old but trusty server and the mythtv-setup appears to use some sort of technology that old cleatus` isn't capable of displaying.
 
Tried 9.10, reverted back to 9.04 due to stability issues.
 
Thanks

---

### Post by ian dobson on 2010-04-06
Hi,

If you have a web server installed o your backend why not use phpMyAdmin, other than that you can edit the settings table by manualy firing SQL queries at it using mysql from theterminal prompt.

Have a look at this thread, from about post 18:- [http://ubuntuforums.org/showthread.php?t=1339102&page=2](http://ubuntuforums.org/showthread.php?t=1339102&page=2)

Regards
Ian Dobson

---

### Post by OpenHeadWound on 2010-04-06
Thanks Ian, was able to install myphpadmin using this tutorial
 
[http://http://chadaphone.wordpress.com/2009/06/02/installation-php-apache-mysql-phpmyadmin-in-ubuntu-9-04/](http://http://chadaphone.wordpress.com/2009/06/02/installation-php-apache-mysql-phpmyadmin-in-ubuntu-9-04/)
 
Changed to the mythconverg DB and edited the IP settings.  We'll see if I can get the front end connected now...
 
Thanks again!

---

