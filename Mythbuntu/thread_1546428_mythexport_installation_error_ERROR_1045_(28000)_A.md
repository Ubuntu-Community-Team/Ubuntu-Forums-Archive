---
title: "mythexport installation error: ERROR 1045 (28000): Access denied for user"
date: 2010-08-05
forum: Mythbuntu
---

### Post by morkunas on 2010-08-05
Trying to install mythexport using Ubuntu Software Center and sudo apt-get install mythexport I get the same error.  Yes i did use sudo dpkg --purge mythexport after each installation, but the same result

ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)  dpkg: error processing mythexport (--configure):   subprocess installed post-installation script returned error exit status 1

I have seen this issue discussed in other threads but I did not come across the solution.  I do not know if this relates but I checked mysql.txt file and there is an entry for DBPassword.  Should this be blank?  I am afraid to remove it, fearing that it would cause other problems.

Andrew

---

### Post by Rotzooi on 2010-08-13
The mythexport installation script doesn't take the information from mysql.txt but from answers given during a (previous) installation.

---

### Post by nickrout on 2010-08-13
which purge SHOULD fix!

---

