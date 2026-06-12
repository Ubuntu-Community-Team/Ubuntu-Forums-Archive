---
title: "Error -Can't access phpmyadmin ,in xampp."
date: 2013-06-10
forum: Myanmar Team
---

### Post by Htut Myat on 2013-06-10
Got the error after installing Xampp ,and when enter the phpadmin ([http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)) .
I can't access .

Error -Can't access phpmyadmin ,in xampp.
Wrong permissions on configuration file, should not be world writable!

---

### Post by Htut Myat on 2013-06-10
Solution-change the permissions of /phpmyadmin/config.inc.php to not be world writable 
(i.e. chmod 755 config.inc.php, or by using your FTP client).

---

