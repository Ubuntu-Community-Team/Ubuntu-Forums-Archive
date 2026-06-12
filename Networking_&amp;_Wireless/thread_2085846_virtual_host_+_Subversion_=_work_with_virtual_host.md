---
title: "virtual host + Subversion = work with virtual hosting"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by Citromon on 2012-11-19
I use Ubuntu 12.10 64 bit and I want make convenient environment for  backuping of my site and it's database of real hosted site (not  dedicated server).

I have this error:
```

apache2: Syntax error on line 260 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/conf.d/svn: /etc/apache2/conf.d/svn:1: <Location> was not closed. Action 'configtest' failed. The Apache error log may have more information.    ...fail!
```I have installed RabbitVCS, php, mysql, phpmyadmin.
Maybe RabbitVCS  can cause the error?

---

### Post by kevinwincott on 2012-11-19
the error is in /etc/apache2/conf.d/svn

can you post a copy of this as it is now?

---

### Post by Citromon on 2012-11-19
```
<Location "/svn/">
DAV svn
SVNPath /home/citromon/localhost/svn/
AuthType Basic
AuthName "SVN Repositories"
AuthUserFile /etc/apache2/svn.htpasswd
Require valid-user
</Location>
```

---

### Post by Citromon on 2012-11-19
Any ideas?

---

### Post by Citromon on 2012-11-20
Could RabbitVCS couse the problem?

---

