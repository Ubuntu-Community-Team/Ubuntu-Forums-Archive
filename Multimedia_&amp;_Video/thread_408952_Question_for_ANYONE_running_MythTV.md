---
title: "Question for ANYONE running MythTV"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by djseto on 2007-04-14
According the MythTV wiki: URL:[http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance#Optimize_the_Database](http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance#Optimize_the_Database)

there should be a Perl script to optimize the DB. I dont have that file anywhere on my disk and I dont have the /usr/share/doc/mythtv-0.20/contrib/optimize_mythdb.pl

directory structure. I have /usr/share/doc/ , but I dont have Mythtv-0.20. I have a few MythtTV folders, but none of them contain a subfolder called "contrib"

I did a pretty standard install of MythTV on Ubunutu 6.10. I dont have this file, does someone know where I can find it or can you post the .pl code up so I can copy it?

---

### Post by Titus A Duxass on 2007-04-14
> I did a pretty standard install of MythTV  What exactly was your pretty standard install?

Did you follow a recognized How-To?

---

### Post by djseto on 2007-04-14
I did this install: [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

If you have the file, can you copy the code.

---

### Post by NT4usB on 2007-04-14
You can optimize the DB via your browser using phpmyadmin.
Login to localhost.
Select mythconverg DB.
Click 'check tables having overhead' (down at the bottom)
Pull down the 'With Selected' box to Optimize table(s).

---

### Post by majoridiot on 2007-04-14
```
$ wget "http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/optimize_mythdb.pl?format=txt" -O optimize_mythdb.pl
```

anything that is supposed to be in the contrib directory can be found at: [http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib](http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib)

---

### Post by djseto on 2007-04-16
I got the file ,but when I try to run it I get:

Can't locate MythTV.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at optimize_mythdb.pl line 15.
BEGIN failed--compilation aborted at optimize_mythdb.pl line 15.


What does this mean? I have Perl installed.

---

### Post by djseto on 2007-04-16
bump

---

### Post by superm1 on 2007-04-17
Edgy packages didn't include the contrib directory.  Starting with feisty, see
/usr/share/doc/mythtv-backend/contrib for all scripts.  

For the edgy packages, the appropriate link is this for the contrib script:
```
wget "http://svn.mythtv.org/trac/browser/branches/release-0-20-fixes/mythtv/contrib/optimize_mythdb.pl?format=txt" -O optimize_mythdb.pl

```

Your running into the above issue I believe from using trunk.

---

### Post by majoridiot on 2007-04-17
sorry for the bad link... superm1's link is the one that you want. :)

---

### Post by Roebi on 2007-04-17
Hello,

what does the script actually do, and for those who have tested it, have you seen any improvement?

I spotted that same wiki page today, but it does not give much detail on what it is good for.
Any feedback would be welcome.

Kind regards,

Roebi

---

### Post by superm1 on 2007-04-17
It should speed up database access.  For people who have very large databases (say been recording for the last few years), it will probably speed up access.

---

### Post by djseto on 2007-04-17
Thanks. It works now!

---

