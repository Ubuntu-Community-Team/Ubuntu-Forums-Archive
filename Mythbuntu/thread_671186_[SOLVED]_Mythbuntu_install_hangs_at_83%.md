---
title: "[SOLVED] Mythbuntu install hangs at 83%"
date: 2008-01-18
forum: Mythbuntu
---

### Post by gthieme on 2008-01-18
My Mythbuntu install hangs at 83%. I got the following error message in /var/log/messages:
Jan 18 00:52:48 ubuntu mythbuntu:    /etc/rc5.d/S20ssh -> ../init.d/ssh
Jan 18 00:52:48 ubuntu mythbuntu: df: Warning: cannot read table of mounted file systems: No such file or directory
Jan 18 00:52:48 ubuntu mythbuntu:  * Starting MySQL database server mysqld
Jan 18 00:52:50 ubuntu mythbuntu:    ...done.
Jan 18 00:52:50 ubuntu mythbuntu:  * Checking for corrupt, not cleanly closed and upgrade needing tables.
Jan 18 00:52:50 ubuntu mythbuntu: /tmp/db_setup: 45: Syntax error: ")" unexpected (expecting "fi")
Jan 18 00:52:50 ubuntu python: log-output -t ubiquity umount /target/cdrom
Jan 18 01:10:05 ubuntu -- MARK --
Jan 18 01:30:05 ubuntu -- MARK --

I am writing this email from the install OS. Is it possible to fix the problem and force the install to continue?

Thanks,
Geoff

---

### Post by ian dobson on 2008-01-18
Hi,

Check your install CD is OK.
Check your ram.
Check your harddisk.

What hardware are you using?

Regards
Ian Dobson

---

### Post by superm1 on 2008-01-18
I'd suspect you chose a mysql password with spaces.  I believe someone else ran into this, but still hasn't filed a bug on it.  Can you please file a bug and try a password without spaces?

---

### Post by gthieme on 2008-01-18
> **superm1 said:**
> I'd suspect you chose a mysql password with spaces.  I believe someone else ran into this, but still hasn't filed a bug on it.  Can you please file a bug and try a password without spaces?

Thanks, that was it. I had a ")" in the password, so I guess it doesn't support ")" or " " ... giving no warning message when these chars are entered. I'll file a bug.

Thanks,
Geoff

---

### Post by ChuckMcB on 2009-01-20
Ditto, tried to use !"£ as part of the mysql password and my install stuck at 83%. [Looks like it's been logged]("https://bugs.launchpad.net/mythbuntu/+bug/160368").

---

