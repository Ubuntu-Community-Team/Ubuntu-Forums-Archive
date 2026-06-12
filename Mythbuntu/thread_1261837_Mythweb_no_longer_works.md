---
title: "Mythweb no longer works"
date: 2009-09-09
forum: Mythbuntu
---

### Post by Eldis on 2009-09-09
I have no idea when I broke it or what caused it to break but it's been some weeks.

This is the error message I get:

> Database Setup Error

The database environment variables are not correctly set in the
webserver conf or .htaccess file. Please read through the comments
included in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README and INSTALL files.

I have tried to figure this out on my own a bit and checked that mod_env is available.

What else could I check ?

I have mythbuntu 9.04 and mythweb installed and configured via mythbuntu control center. I have various other sources added such as Avenard repo for backported VDPAU.

---

### Post by azmyth on 2009-09-09
A few times when I was using Avenard's it would overwrite my mythweb.conf file. I'd check in there to make sure you db credentials haven't been changed.

/etc/apache2/sites-available/mythweb.conf

---

### Post by Eldis on 2009-09-09
> **azmyth said:**
> A few times when I was using Avenard's it would overwrite my mythweb.conf file. I'd check in there to make sure you db credentials haven't been changed.

/etc/apache2/sites-available/mythweb.conf

Thanks, that tip was spot on. Took me about 10 sec to fix it now that I knew where to look. Problem was that setenv db_server was "" and it should be localhost. 


The root cause is this: apache2: ```
Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

apache keeps bitching about that everytime I start the service. Any idea where I could set that ServerName ?

---

### Post by OldGaf on 2010-01-09
> **Eldis said:**
> Thanks, that tip was spot on. Took me about 10 sec to fix it now that I knew where to look. Problem was that setenv db_server was "" and it should be localhost. 

SNAP!

I have been trying to figure this one out for some time..... thanks m8 !

---

