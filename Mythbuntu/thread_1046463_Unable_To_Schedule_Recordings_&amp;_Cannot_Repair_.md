---
title: "Unable To Schedule Recordings &amp; Cannot Repair DB"
date: 2009-01-21
forum: Mythbuntu
---

### Post by PeteCress on 2009-01-21
I'm in somewhat the same situation as the OP in " [SOLVED] Unable to schedule recordings after power outage " except I cannot correlate the onset with a power failure and I am unable to repair the DB.

This problem has plagued me a number of times on totally different installs.

Specifically, when I try to schedule a recording in Program Guide the look of the program's cell does not change to indicate that it is scheduled and when I check up on it the next day it has not been recorded.

Looking at the FrontEnd log file, I don't see anything even remotely indicative of the code throwing errors.

When I try to repair the DB:
---------------------------------------------------------
x@MythBpx:~$ sudo mysqlcheck -u root -p --auto-repair --check --optimize --all-databases

Enter password:

mysqlcheck: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect

---------------------------------------------------------

I tried the password for the Linux user and I tried the DB password as shown in MythTv Frontend's "General" setup screen.

Tried each a half-dozen times, so I'm 99 44/100ths percent sure it isn't a typing/spelling issue.

I'm pretty much clueless as a Linux user, but I've struggled with quite a few other mysterious (to me...) MythTV problems and my gut feeling is that there's some kind of permission/access issue that I don't know about - but which is common to a number of seemingly-different problems.

Can anybody elucidate?

---

### Post by uncle hammy on 2009-01-21
You'll need to either set a password for root, or log in to mysql with 'mythtv' as your user, and the password from the "General" setup screen.

If you're going to do all-databases, you'll need to be root...

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

are the two commands that will allow you to configure your database, including setting the root password.  Ensure you enter the same password for the mythtv user that you are currently using (the "General" one), or you'll have to change it in all your frontends...or sun the commands again, and get it right.

The other thing you can do is do the repair from Mythweb.

Hope that helps.

---

### Post by PeteCress on 2009-01-21
> **uncle hammy said:**
> The other thing you can do is do the repair from Mythweb.

MythWeb is the most functionality with the least investment of user effort that I've ever seen.

Thanks.

Still have the same problem after doing "Repair" and "Optimize", but right now still kind of overwhelmed at the amount of functionality in MythWeb.

I'm going to try the

. .  sudo dpkg-reconfigure mythtv-database
. .  sudo dpkg-reconfigure mythtv-common

thing next.

---

### Post by PeteCress on 2009-01-22
> **PeteCress said:**
> I'm going to try the

. .  sudo dpkg-reconfigure mythtv-database
. .  sudo dpkg-reconfigure mythtv-common

thing next.

x@MythBpx:~$ sudo dpkg-reconfigure mythtv-database
 * Starting MySQL database server mysqld                                 [ OK ] 
Failed to connect to database: Access denied for user 'x'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database


Tried several times 99 44/100% sure I didn't fat-finger the PW.

---

