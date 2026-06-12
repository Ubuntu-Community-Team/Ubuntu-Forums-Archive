---
title: "Schema is 2 versions behind"
date: 2009-12-31
forum: Mythbuntu
---

### Post by cabbage on 2009-12-31
Hi,

I've just installed the mythtv frontend on a Windows XP laptop from here:

[INDENT][http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)[/INDENT]

using the 0.22-fixes 22888 version.

When it connects to my mythbuntu backend I get the error that the schema is two versions behind.

The backend is running 0.22 from the PPA repo ver 22994.

So why is my schema not up to date? Can it be manually updated?


Thanks,

Cabbage.

---

### Post by cabbage on 2009-12-31
Just tried another update and got this:

```
Setting up mythtv-database (0.22.0+fixes23034-0ubuntu0+mythbuntu2) ...
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database

```

I've checked that the debian-sys-maint user/password in /etc/mysql/debian.cnf is correct.

Help?

---

### Post by cabbage on 2010-01-01
Happy New Year!

---

### Post by cabbage on 2010-01-01
OK - the dpkg-reconfigure problem was because the debian-sys-maint user did not have enough permissions:

> mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY '***';
ERROR 1044 (42000): Access denied for user 'debian-sys-maint'@'localhost' to database 'mythconverg'


I don't know why this is, but giving the user all privileges now allows it to work. Maybe something in mysql has changed?!?

Anyway, I guess this doesn't answer why I'm two schema versions behind... Is there a specific plugin that contains the update?

---

