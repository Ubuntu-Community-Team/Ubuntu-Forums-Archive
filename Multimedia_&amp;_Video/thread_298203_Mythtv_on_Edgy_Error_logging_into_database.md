---
title: "Mythtv on Edgy Error logging into database"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by linux-convert on 2006-11-12
Ok I am trying to install Myhtv on on Edgy and I am receiving an error I am unsure how to fix...

Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database


Since root is being denied access to the database I really can't go any farther.....

---

### Post by superm1 on 2006-11-12
Do you have mysql-server already installed on the machine your installing the database on?  It's not a dependency of the "mythtv" package or even "mythtv-database", but if you are setting up your mysql server on the same box as your mythtv-backend, you need it installed.

---

