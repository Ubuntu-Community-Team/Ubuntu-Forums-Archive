---
title: "configuration of wifidog"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by chupacuph on 2012-07-22
hallo everyone,,i have installed wifidog on my ubuntu,, i'm using ubuntu 11.04,, but when i'am configure wifidog i got errors on step database connection..this is the result after configure database acces :

Trying to open a Postgresql database connection : Unable to connect  to database!  Please make sure the server is online and the database  "wifidog" exists. Also 'postgresql.conf' and 'pg_hba.conf' must allow  the user "5432" to open a connection to it on host "wifidog" port 0 to  continue.  See the error above for clues on what the problem may be.
Please go back and retry with correct values, or fix your server configuration.


what's wrong ?? anyone can help me please .. thank you ..

---

### Post by richpri on 2012-07-22
Try the wifidog help site.

[http://dev.wifidog.org/wiki/Contact%20/%20Support](http://dev.wifidog.org/wiki/Contact%20/%20Support)

---

### Post by chupacuph on 2012-07-24
i still got stag here ,, my localhost can't acces the database too .. and the result is like this :
**I am unable to retrieve the schema version. Either the wifidog  database hasn't been created yet, the postgresql server is down, or  pg_hba.conf does not allow your web server to connect to the wifidog  database.**

**Error was: Unable to connect to the database at host=localhost port=5432 dbname=wifidog user=wifidog password=***********

**Try running the [installation script]("http://localhost/install.php").**



i can't open port 5432 .. what's wrong ??

---

