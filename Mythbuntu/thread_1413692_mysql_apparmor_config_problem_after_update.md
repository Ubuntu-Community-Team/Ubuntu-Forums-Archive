---
title: "mysql apparmor config problem after update?"
date: 2010-02-22
forum: Mythbuntu
---

### Post by ZedThou on 2010-02-22
I'm curious to know if anyone else has seen this. I was suddenly having all sorts of problems watching videos, with a bunch of invalid database connection  messages in the frontend log. Meanwhile, dmesg was showing a series of these

```

[   20.369673] type=1503 audit(1266794314.380:22): operation="open" pid=1159 parent=1158 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

```after adding the following to /etc/apparmor.d/usr.sbin.mysqld, everything is back to normal.

```

  /sys/devices/system/cpu/ r,

```Is this a known problem, or did something really odd happen to my system (I believe I recently updated, and I also had a power blip yesterday which rebooted the combined front/backend)?

---

### Post by theDaveTheRave on 2010-02-23
ZedThou,

I've seen some strange errors in MySQL lately.

I've not been able to determine if the problem is with apparmor or with the  debian-system-maintenence user.

If you have some error messages with this users details within them check out [this thread]("http://ubuntuforums.org/showthread.php?t=1373144") to see if they are somehow similar.

If so it may be an issue with how mysql updates are coming across? Have you recently done an upgrade?

David

---

### Post by ian dobson on 2010-02-23
Hi,

Looks as if ubuntu/mythbuntu as set apparmor to run in complain mode. It won't block anything, it'll just winge all the time :)

Regards
Ian Dobson

---

### Post by rgunn on 2010-02-24
> **ZedThou said:**
> I'm curious to know if anyone else has seen this. I was suddenly having all sorts of problems watching videos, with a bunch of invalid database connection  messages in the frontend log. Meanwhile, dmesg was showing a series of these

```

[   20.369673] type=1503 audit(1266794314.380:22): operation="open" pid=1159 parent=1158 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

```after adding the following to /etc/apparmor.d/usr.sbin.mysqld, everything is back to normal.

```

  /sys/devices/system/cpu/ r,

```Is this a known problem, or did something really odd happen to my system (I believe I recently updated, and I also had a power blip yesterday which rebooted the combined front/backend)?

I updated as well and mysql would not start...

Feb 25 10:08:06 rgunn-ub9 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Feb 25 10:08:06 rgunn-ub9 mysqld: 100225 10:08:06 [Warning] Can't create test file /var/lib/mysql/rgunn-ub9.lower-test
Feb 25 10:08:06 rgunn-ub9 mysqld: 100225 10:08:06 [Warning] Can't create test file /var/lib/mysql/rgunn-ub9.lower-test

So i found this post and changed apparmor accordingly

[http://planet.mysql.com/entry/?id=22693http://planet.mysql.com/entry/?id=22693](http://planet.mysql.com/entry/?id=22693http://planet.mysql.com/entry/?id=22693)


all works fine now but i was completely stumped initially

---

