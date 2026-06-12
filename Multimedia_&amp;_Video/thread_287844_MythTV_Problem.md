---
title: "MythTV Problem"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by n00b@linux on 2006-10-29
I'm new to MythTV.  I have never installed or configured it before.
I downloaded the packages from the Dapper repositories, then I upgraded Dapper to Edgy.  I presume as part of this upgrade that the MythTV packages were upgraded as well.

Anyway, I cannot set up MySQL database.  I got the following error reported by Synaptic:

```
Setting up mythtv-database (0.20-0.2 ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
```So I did as suggested and ran 'sudo dpkg-reconfigure --force mythtv-database'.  I left the default MySQL administrator account name as 'root'.  I left the MySQL password blank as recommended.  However, I still the get the same error:

```
n00b@ubuntu:~$ sudo dpkg-reconfigure --force mythtv-database
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
n00b@ubuntu:~$ 

```What am I doing wrong?  Can someone please help me?  ](*,)

---

### Post by jaymode on 2006-10-29
Hmm well I did not have that problem, mine was denial for 'mythtv'@localhost. I believe that something had changed from dapper to edgy packages. You may want to back up your database assuming you were using myth in dapper.

One thing I would try is to change your mysql permissions. See this page:
[http://mythtv.org/docs/mythtv-HOWTO-6.html](http://mythtv.org/docs/mythtv-HOWTO-6.html)



If that does not work, then I would remove all of the mysql packages and mythtv packages and fresh install. This may remove all your database info which is why I said to back it up. Hopefully you dont have to do this. This should be a last resort.

---

### Post by vanhoja on 2006-10-29
n00b:

I've been futzing with MythTV on and off again for the last few weeks, and just tried installing Myth this morning on Edgy-x86_64.  I ran into the *exact* same issue as you, and I got around it.  I wish I was taking notes (this was pre-Sunday-Morning-coffee computing), so my recollection of what I did is a little fuzzy... but here goes...
MySQL-client is installed along with MythTV when you use Synaptic.  The server, OTOH, isn't.  Make sure that MySQL-server is installed, and, along with it, install phpMyAdmin. To make sure we're starting with a clean slate, **uninstall **mythtv-database as well.  We can fix that later.
After installing these two, fire up Firefox and go to your localhost address, 127.0.0.1, and click on phpmyadmin.  If you just installed MySQL-server, log in using root, leaving the password field blank. If MySQL-server was installed previously, log in as root and use the password you assigned the root account when MySQL was installed. (More than likely, and like my situation, leving the password field blank works for this.) After logging in, you should see a list of menu items in the main window, one of which is Priveleges.  Click on that, and you'll see a table of all MySQL users that were setup already.  Hopefully, you should see mythtv and root listed as users (you might see a pair of each of them).  What needs to be done here is that you need to ensure the passwords assigned to both root and mythtv are set correctly (or at least to something you know!).  Click on the icon that looks like a little man with a pencil (the Edit icon) on the far right of the line for root (if you have two, like root@localhost or root@ubuntu, just choose one or the other).  The next screen will show all of the priveleges assigned to root, and about halfway down the page is a line to change the password.  Enter a new password into each of the Password: and Re-Type lines...this will be your root password for MySQL, so choose something you're familiar with... and click go.  The query will run, and hopefully will say "Successful".  If you had two entries for root on the Priveleges screen, click on the Priveleges tab at the top of the screen and repeat the same process for your other root entry.  After changing your root(s) password(s), now click on the Priveleges tab at the top, and click on the Edit icon for your mythtv user (if you have two, just pick one, same as you did for root).  Change the password for you mythtv user to **mythtv** . If you had two entires for mythtv, click on Priveleges tab and repeat the process for the other user - make sure the password is mythtv.  After that, look to the column on the left side of your phpMyAdmin screen - you should see a house.  Click on that to bring you back to the main menu.  Now, look for the link that says Restart MySQL, and click on it.  This will refresh and save all of the changes you've made.  Also note... if, after changing your root passwords you're brought back out to the login screen for phpMyAdmin, just log back in as root with your MySQL root password (the one you changed to something you remember, right?!?) and pick up where you left off.
Let's see... from here, after restarting MySQL, you should be back at the main phpMyAdmin menu.  At this point, look at the left-hand column again for an Exit icon, and click on it.  You should be all done with MySQL at this point.  Now, open up a terminal and re-run the command to reconfigure the package:

dpkg-reconfigure --force mythtv-database

If you get a configuration screen asking for MySQL's root account, go ahead and use root, and when prompted for the password, use the one you created for root in phpMyAdmin.  After this, now go back to Synaptic and re-install mythtv-database.  Hopefully, it should install without hiccups this time.

I am by no means a linux guru (yet!), but this worked for me, and the usual Your Mileage May Vary rule applies.  I can only hope that this is my first successful contribution to the Ubuntu community, and that it certainly won't be my last!

Let me know if this worked...

---

