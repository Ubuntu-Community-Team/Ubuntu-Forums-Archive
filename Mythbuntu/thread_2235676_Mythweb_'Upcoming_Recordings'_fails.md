---
title: "Mythweb: 'Upcoming Recordings' fails"
date: 2014-07-22
forum: Mythbuntu
---

### Post by tobiz on 2014-07-22
I'm running mythbuntu on 12.10 with all updates installed (I assume 12.10 is still in support, if not ignore this post). Today I got "Warning at /usr/share/mythtv/mythweb/modules/tv/upcoming.php, line 91:
!!NoTrans: Invalid argument supplied for foreach()!!".  I've never had this before.  Searching ubuntu forums suggests this had been reported in 2011 on 2:0.24.0+fixes.20110516.b5a3805-0ubuntu0mythbuntu1, I'm running 2:0.25.2+fixes.20120802.46cab93-0ubuntu1.12.10 (which Synaptic thinks is the latest). Any ideas how to fix welcome.

---

### Post by khPWXxF on 2014-07-22
[FONT=Calibri][SIZE=3][COLOR=#000000]Google shows:
[/COLOR][/SIZE][/FONT][http://www.mythtv.org/pipermail/mythtv-users/2012-July/336598.html](http://www.mythtv.org/pipermail/mythtv-users/2012-July/336598.html)

The utility optimize_mythtdb.pl both optimizes and repairs the database.  It's described in the wiki.
Suggest you find it on your system with:

```
locate optimize_mythdb.pl
``` 

then execute it.

Does this fix it?
Phil

---

### Post by tobiz on 2014-07-22
Phil, thanks for that.  Located and run as root optimize_mythdb.pl, mythweb upcoming recordings still reports same problem.

I notice [https://code.mythtv.org/trac/attachment/ticket/10142/mythweb-php-warning.patch]("https://code.mythtv.org/trac/attachment/ticket/10142/mythweb-php-warning.patch") makes a change in this area.  I don't understand why this code change is made but looks like the problem (except for line numbers not quite right but I guess this is minor)

---

