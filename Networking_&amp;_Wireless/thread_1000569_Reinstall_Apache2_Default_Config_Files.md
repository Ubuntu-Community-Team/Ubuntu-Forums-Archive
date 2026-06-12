---
title: "Reinstall Apache2 Default Config Files"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by lateralus01 on 2008-12-03
For some reason when I rebooted my server apache2 would not start.  It gave no error message, but webmin reported it hadn't actually started and when I scanned my ports, 80 was not open.  Well I played around until eventually I uninstalled apache2 and removed /etc/apache2 and /var/log/apache2.  I then ran "apt-get install apache2".  Apache2 was installed, but the default configuration files were not.  Does anyone know where I can either download the default config files or do a fresh install of apache2?

Thanks,

Lateralus01

---

### Post by lateralus01 on 2008-12-03
I've tried compiling from source but the default files are still not there...

---

### Post by superprash2003 on 2008-12-03
go to the synaptic package manager.. do a COMPLETE REMOVAL and install again

---

