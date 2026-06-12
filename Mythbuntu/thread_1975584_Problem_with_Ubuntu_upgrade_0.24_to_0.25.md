---
title: "Problem with Ubuntu upgrade 0.24 to 0.25"
date: 2012-05-07
forum: Mythbuntu
---

### Post by Daminator on 2012-05-07
Hello all,

Well, sometimes it goes smoothly, sometimes not. A few days ago, I switched over my Ubuntu install of mythtv (Mythbuntu on top of an Ubuntu setup) from the 0,24 repositories to the 0.25 repositories. After running the Update Manager, it suggested that I do a 'partial upgrade'.

Most of the update went without a hitch, except for upgrading the mythtv.cnf file. I got a message asking me if I wanted to keep the current file or accept the changes. I've been stung by this sort of thing before, so I cut and pasted the differences. Here's what was displayed during the install:

--- /etc/mysql/conf.d/mythtv.cnf    2012-04-18 20:27:49.000000000 +0100
+++ /etc/mysql/conf.d/mythtv.cnf.dpkg-new    2012-05-03 00:07:41.000000000 +0100
@@ -1,2 +1,3 @@
 [mysqld]
-bind-address=0.0.0.0
+#bind-address=0.0.0.0
+max_connections=100

I believe I told it to keep the current file. Here's the contents of my mythtv.cnf file as it is today:

[mysqld]
bind-address=0.0.0.0
max_connections=100

The install then continued as normal and finished. Now the fun begins

I tried to run the frontend (on the same system) and a little message at the bottom of the screen (gnome) kept popping up saying that the frontend was restarting. This popped up every few seconds, so it was in some sort of loop.

I rebooted and still had the same problem.

If I try to go to the backand setup, I get asked if I would like to start the mythtv backend, which implys that the back end isn't even running any more. I click on 'yes' and am then asked if I would like to run mythfilldatabase. I click 'yes' again. At no point am I taken into the backend setup screens.

If I try to go into the backend setup again, I get asked if I want to run mythtv backend again etc etc.

I've just had a look at /var/log/mythtv/mythbackend.log and it doesn't seem to have had an entry since 3rd May. The /var/log/mythtv/mythfrontend.log file hasn't had an entry since the 2nd May.

Where can I look for some information that could help to fix this?

Thanks
Damian

---

### Post by singedwings on 2012-05-18
What happens when you try to start mythtv backend setup? It may sound drastic but you could simply reinstall the mythtv packages. Backup your database first - or if you have restored an earlier database did this  have settings within it that are causing problems? Or is mysql screwed up? Is everything correct with the following files```
/etc/mysql/my.cnf
/etc/mythtv/config.xml
/home/user/.mythtv/config.xml
/home/user/.mythtv/mysql.txt
```

---

