---
title: "Mythweb"
date: 2009-05-19
forum: Mythbuntu
---

### Post by jolly79 on 2009-05-19
Hi Guys

I have just upgraded to myth daily builds version fixes 20508
and almost everything is running smooth but my mythweb keeps saying this:

Database Setup Error
The database environment variables are not correctly set in the
webserver conf or .htaccess file. Please read through the comments
included in the file and set up the db_* environment variables correctly. 

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README and INSTALL files. 
--------

I have triede changing the stuff in the mythweb.conf.apache.
Isen´t this normally auto setup??

---

### Post by jolly79 on 2009-05-19
Figured it out :-)

There was missing info here: sudo nano /etc/apache2/sites-available/mythweb.conf

Just added localhost in where it said setenv db_server, the a restart of apache2 (sudo /etc/init.d/apache2 restart) and it was running.

---

