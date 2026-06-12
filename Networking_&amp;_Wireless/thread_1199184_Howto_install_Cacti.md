---
title: "Howto install Cacti"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by metalfan_ on 2009-06-28
Hi,

aptitude installed cacti to /usr/share, do i copy/link/whatever it to /var/www ?

---

### Post by jhannah on 2009-06-28
The default installation of Cacti should create a symlink in /etc/apache2/conf.d to /etc/cacti/apache.conf which setups the permissions for the directory and creates a global Alias. Thus, going to /cacti should bring up the interface. You can, of course modify this to suit your needs but basically the web root for Cacti is /usr/share/cacti/site. If you don't make use of the default Apache conf.d configuration file, make sure you include analogous directives to what it provides for Catci to work correctly.

---

### Post by metalfan_ on 2009-06-28
Ah, forgot to look for apache2.conf changes...thx.

---

### Post by LinuxGold on 2009-07-24
I installed cacti using apt-get install cacti and it worked beautifully.  I found out that I am running cacti 0.8.7b and latest is 0.8.7e.  Is there any 0.8.7e in deb package that I can install?  What defaults do Ubuntu use (paths) for cacti so I can install manually if there isn't any deb for 0.8.7e?

Thanks.

---

### Post by LinuxGold on 2009-08-19
Bump

---

