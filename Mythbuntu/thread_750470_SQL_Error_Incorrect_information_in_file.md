---
title: "SQL Error: Incorrect information in file"
date: 2008-04-09
forum: Mythbuntu
---

### Post by RobJohnston on 2008-04-09
Hi all, somthing went wrong with my myth box and I've lost both the desktop and now mythweb. I think something happened to mysql.

When I log on to mythweb I get:
```
    datetime:  2008-04-09 20:03:30 (BST)
    errornum:  256
  error type:  User Error
error string:  SQL Error: Incorrect information in file: './mythconverg/weatherscreens.frm' [#1033]
    filename:  /usr/share/mythtv/mythweb/objects/Database/Query/mysql.php
  error line:  83
```

Googling this leads me to check my.cnf but I can't see anything wrong.

Looking thru phpMyAdmin I have three weather tables that look broken.

I'd quite like to get mythweb working again to manage the box and save a few things before I reinstall.

Any ideas why these tables have broken and how I can fix it?

Thanks, Rob.

---

### Post by ian dobson on 2008-04-09
Hi,

Looks as if your Mysql db is corrupt. It could happen if you had an unclean shutdown.

One thing to try is repairing the DB using PHPadmin, select the DB then select Operations then repair table.

Hope this helps
Regards
Ian Dobson

---

### Post by soho on 2008-10-14
I had the same problem (among numerous others) after a power outage. It turned out that the /tmp directory had changed write permissions. chmod 1777 /tmp and a reboot solved the problem.

---

