---
title: "Mythbuntu 9.10 Frontend won't start"
date: 2010-02-05
forum: Mythbuntu
---

### Post by dualboot on 2010-02-05
Hi All,
My Frontend will no longer start.  I re-booted after an update, and it hung on a grub menu.  Nothing would shift it - hand to power it off.  Tried several times, 'till I figured out that it didn't recognise a USB keyboard at that stage (wierd because bios and normal gui do !)

Anyway, now frontend won't start.  I get this from frontend log.

```
justin@sonata-desktop:/var/log/mythtv$ tail mythfrontend.log
QMYSQL3: Unable to prepare statement
Database error was:
Incorrect file format 'displayprofilegroups'

2010-02-05 19:18:05.379 DB Error (get_profiles):
Query was:
SELECT name FROM displayprofilegroups WHERE hostname = ? 
Bindings were:
:HOST=sonata-desktop
No error type from QSqlError?  Strange...
justin@sonata-desktop:/var/log/mythtv$ 

```

also now noticed the mythweb is broken I get

```
Warning: require(modules/_shared/tmpl/tmpl/header.php) [function.require]: failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23

Fatal error: require() [function.require]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
```

Any suggestions would be welcome.

---

### Post by dualboot on 2010-02-06
I've configured PHPMyAdmin and that can open the mythconverg database, but I don't really know what I'm looking for.

I could run the backend configuration utilitity - it can't see my capture cards any more, but I'm reluctant to start re-working things without really knowing what I am doing.

Any help would be appreciated.

---

