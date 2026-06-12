---
title: "MythWeb Database Setup Error"
date: 2008-08-19
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-19
When I try "http://mythtv/mythweb/status" from my browser, I get this verbage:> Database Setup Error

The database environment variables are not correctly set in the
webserver conf or .htaccess file. Please read through the comments
included in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README and INSTALL files.

which was not very helpful for me.. (What REAME??.INSTALL what?)  I then tried 
```
sudo apt-get remove --purge  mythweb*
```
that resulted in some messages about non-empty directories. I followed that by 
```
sudo apt-get install mythweb
```
Same error message.

I also found the text file  **/var/www/mythweb/INSTALL**. I haven't been though it completely.  Some of the references apparently do not apply to MythBuntu.

The error showed up after I used MCC to install the Ubuntu Desktop and added an external USB connected input card.

Any ideas?

---

### Post by LarryJ2 on 2008-08-23
Guess we can show this as "Solved".  After installing mythbuntu on another box and comparing the two for two days,  I gave up.  Now after a complete HD wipe and replacement/re-installation with mythbuntu 8.04-1,  everything seems back working, except for WatchTV which goes black for about 30 seconds then dumps back to the mythbuntu menu.

---

