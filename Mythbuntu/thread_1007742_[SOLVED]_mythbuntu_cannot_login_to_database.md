---
title: "[SOLVED] mythbuntu: cannot login to database"
date: 2008-12-10
forum: Mythbuntu
---

### Post by ub40d on 2008-12-10
A few months ago my mythbuntu box filled up
with recordings and stopped working. I deleted
a few large files but no joy. At the time I
had no spare time to try and fix it so I just
left it. Now I'd like to get it going again,
preferably without losing all the past
recordings I haven't watched yet.

When I boot up, or when I do (menu)
applications / multimedia / mythtv frontend, I
get the infamous blue screen that asks for a
language, then says no upnp backends found,
and then gives two pages of questions about
database configuration.

All the entries in there are the same as
/etc/mythtv/mysql.txt:

DBUserName=mythtv
DBPassword=xxx
DBName=mythconverg
 
but despite that I get "cannot login to
database? ok" and then it starts again with
the same two pages, until I press escape.

However I can login to the database "by hand"
with that same userid and password: if I go
into a terminal, the following command works

mysql --user=mythtv --password=xxx mythconverg

and takes me to an sql prompt where things
like SHOW TABLES; work and prove that I am
connected to the database.

What else should I do to enable mythtv
frontend to login too using those details?

---

### Post by scary_jeff on 2008-12-10
Just a suggestion as I am certainly no expert on this, but what host are you trying to connect to? If you are using the machines network IP, try localhost or 127.0.0.1. If you are already trying these, try the machines network IP.
In /etc/mysql/ , look in my.cnf for either bind-address or skip-networking [depending on mysql version], to find out if mysql is running on loopback adapter or the actual network adapter. skip-networking being true or 1 implies loopback adapter (as I understand it).

---

### Post by ub40d on 2008-12-10
GENIUS! You fixed it!

I was using the machine name, as it appeared in the shell prompt. I changed it to 127.0.0.1 and hey presto, for the first time the blue config screens didn't end up saying "cannot login to database" and instead they sent me to the familiar mythtv main menu. WELL DONE!

Things weren't quite working there at that point (couldn't watch tv, couldn't see any recordings etc) but a bit of 
 sudo dpkg-reconfigure mythtv-common
 sudo dpkg-reconfigure mythtv-backend
 mythtv-setup
took care of most of that.

I have some more things that need fixing but you definitely solved the problem I described in the original post. (Though no clue why the machine name didn't work for the same purpose; but hey, who cares.)

Thanks a million!

---

### Post by MountainX on 2009-02-24
I'm getting this same error on a brand new Mythbuntu 8.10 install. All the values entered into setup match the values in /etc/mythtv/mysql.txt.

What else could be the problem?

---

