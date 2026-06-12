---
title: "Mythweb Errors"
date: 2009-11-11
forum: Mythbuntu
---

### Post by zzzBrett on 2009-11-11
After installing mythweb, i can navigate to

[http://localhost/mythweb/](http://localhost/mythweb/)

and I see this:

[IMG]http://i36.tinypic.com/59ttvt.jpg[/IMG]


I can then click on mythweb.php, and i see this:

[IMG]http://i38.tinypic.com/our0g7.png[/IMG]

```
Text Error:
Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/db_vars_error.php, line 23:
require(modules/_shared/tmpl/tmpl/header.php) [function.require]: failed to open stream: No such file or directory

Fatal error: require() [function.require]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/db_vars_error.php on line 23
```


Any ideas why?

---

### Post by zzzBrett on 2009-11-12
bump

---

### Post by writ on 2009-11-16
Check the line "bind-address" in /etc/mysql/my.cnf and /etc/mysql/conf.d/mythtv.cnf

It should not be commented out and should be set to the ip address of your myth server.  In my case, I set it to:

bind-address=192.168.0.201 in both files mentioned above. (If you don't know what this number should be, let me know and I can tell you how to figure it out.)

I hope this helps.

---

### Post by CaveMole on 2010-12-03
> **writ said:**
> Check the line "bind-address" in /etc/mysql/my.cnf and /etc/mysql/conf.d/mythtv.cnf
...

I don't have /etc/mysql/conf.d/mythtv.cnf

What might this mean?

I still have this problem...

---

### Post by nickrout on 2010-12-03
> **CaveMole said:**
> I don't have /etc/mysql/conf.d/mythtv.cnf

What might this mean?

I still have this problem...

It is part of mythtv-database, which means you probably haven't installed mythbackend.

---

