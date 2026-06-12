---
title: "audit spamming syslog"
date: 2009-11-28
forum: Mythbuntu
---

### Post by ian dobson on 2009-11-28
Hi All,

I've just upgraded my backend to 9.10 this morning and since then audit is writing a message to the log file every second.

```
Nov 28 18:17:00 alpha2 kernel: [ 8741.187962] type=1502 audit(1259428620.394:17562791): operation="open" pid=4925 parent=1517  profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=103 ouid=103 name="/data/mysql/mythconverg/"
Nov 28 18:17:00 alpha2 kernel: [ 8741.187970] type=1502 audit(1259428620.394:17562792): operation="file_perm" pid=4925 parent=1517 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=103 ouid=103 name="/data/mysql/mythconverg/"
Nov 28 18:17:00 alpha2 kernel: [ 8741.188136] type=1502 audit(1259428620.394:17562793): operation="file_perm" pid=4925 parent=1517 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=103 ouid=103 name="/data/mysql/mythconverg/"
```

Is there an easy way to get rid of this/ change audit so that it doesn't complain about mysqld/mythconverg anymore.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-11-28
Hi All.

Found it. apparmor is installed and the profile for mysqld didn't know that I'm using a different directory for my mysql database /data/mysql (RAID 5 array). So I jus had to edit /etc/apparmor.d/usr.sbin.mysqld adding /data/mysql to the allowed drectories.

Regards
Ian Dobson

---

