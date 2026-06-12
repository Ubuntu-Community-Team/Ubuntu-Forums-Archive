---
title: "Undefined function mssql_connect"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by jcortes on 2009-09-22
I have a script that connects to a MS SQL server and I keep getting 

**Fatal error: Call to undefined function mssql_connect() in /var/www/timeclock/importers/studentimporter.php on line 13**

Im running apache2, php5, etc.

Is there a package i have to install to enable MS SQL support in linux? I know in windows all i had to do was uncomment the php_mssql.dll line.

---

### Post by jcortes on 2009-09-24
Answer: Installing the package **php5-sybase** 

Thanks Me! :)

---

