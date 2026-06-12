---
title: "WebDAV help - permissions mostly"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by 47_MasoN_47 on 2009-03-10
Hi everybody, I've got WebDAV running successfully on a 8.10 LAMP server.  This server was setup to be a development environment for our web applications so that me and a few other guys could work on the web apps in an offline environment.  If WebDAV worked really well we thought about using it for other things as well.

Right now I have successfully shared my first directory and the 3 users I've setup can all add, remove, and edit files in it.  Now, since I'm editing web apps that connect to our MySQL database, I don't want the other guys to be able to see the .php files that connect to the database.  Is there a way that I can restrict access to those files so that only I can view/edit them?

I'm using a htpasswd to setup the user accounts (that's what I read about in the tutorials I used to get it working).

Thanks!

---

