---
title: "Mythbuntu MySQL Time Zone Tables missing"
date: 2013-10-22
forum: Mythbuntu
---

### Post by drifting on 2013-10-22
Just happened tonight after doing a few updates. I was on .27 already so assume the timezone thing had worked fine.

mythtv-backend start/running, process 3110
 is running, but it did mention something about the timezones not being configured ?

Oct 22 23:27:36 mythserver mythbackend: mythbackend[3248]: E CoreContext main_helpers.cpp:547 (run_backend) MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance

Why I do not understand as it was working fine, so I tried the below.

[http://www.mythtv.org/wiki/MySQL_Time_Zone_Tables](http://www.mythtv.org/wiki/MySQL_Time_Zone_Tables)

Followed this howto, but it fails to complete at :- mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root -p<yourpassword> mysql
And just sits there at a ">" prompt.

Now I admit my knowledge is really at it's limits now, so any suggestions welcome.

Paul.

---

### Post by drifting on 2013-10-27
Forget it, guess who was dumb enough to try and enter he command listed into MySQL rather than the command line! Slaps head a wanders off in shame.

---

