---
title: "Problems with running myth.rebuilddatabase.pl"
date: 2008-05-08
forum: Mythbuntu
---

### Post by dinger1986 on 2008-05-08
Hi there,

I am having a problem running myth.rebuilddatabase.pl on a newly installed mythbuntu 8.04 box. 

When I run the command:
sudo ./myth.rebuilddatabase.pl --ext avi

I get the error:
DBI connect('database=mythconverg:host=media','mythtv',...) failed: Can't connect to MySQL server on 'media' (111) at ./myth.rebuilddatabase.pl line 191
Cannot connect to database ()


I have checked the username and the password(from /usr/share/mythtv/mysql.txt) and run: 
mysqlcheck --auto-repair -A -u mythtv -pmypassword.

Is anyone else having problems with it? 

I have looked through forums for the last 2 days and cant find anything.

Regards,
Daniel

---

### Post by dinger1986 on 2008-05-09
Doesnt matter got it to work.

Changed the line:
my $host = hostname;

to
my $host = "localhost";

Just incase anyone else ever has the same problem.

Regards,
Daniel

---

