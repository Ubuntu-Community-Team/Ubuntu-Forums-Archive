---
title: "Upgrade to 10.04 has lost MythTV frontend"
date: 2010-05-09
forum: Multimedia Software
---

### Post by RobertSwipe on 2010-05-09
Since upgrading to 10.04 (Ubuntu), the desktop icon for MythTV front end now gives an error that "No such file or directory found".

At first, the backend failed to start, but I noticed that after the initial reboot following the upgrade, MySQL was not running and this had to be kickstarted manually.

Trying to launch the frontend from the cli gives the message:
"The program 'mythfrontend' is currently not installed.  You can install it by typing: sudo apt-get install mythtv-frontend"

However, if I do this, I then get the message:
"Package mythtv-frontend is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mythtv-backend mythtv-common
E: Package mythtv-frontend has no installation candidate"

If I then do this, I get:
"mythtv-backend is already the newest version.
mythtv-common is already the newest version.
The following packages were automatically installed and are no longer required:
  ubuntu-xsplash-artwork libtotem-plparser12 libopal3.6.4 libpt2.6.4-plugins
  libzip1 libpt2.6.4 odt2txt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."

So does anyone know how can I get my MythTV frontend back again?

---

### Post by RobertSwipe on 2010-05-09
Solved - I was clearly too impatient after upgrading from a copy of the 10.04 Alternate CD.

When I ran Update Manager, it informed me that I needed to run a "Partial Upgrade". So I did that, and although MythTV Front End still failed to start, when I tried:
  sudo apt-get install mythtv-frontend

...it now worked as expected and I now have my MythTV back again - just in time to get to see the latest Doctor Who....

---

### Post by Braik on 2010-05-19
Hi Robert,
 
I write this message because it think you can help me with my problem, I was very shortly runing MythTV in Karmic.
 
I had some problems upgrading Karmic to Lucid so I had to make a clean installation, and now when turn on my computer my MythTV frontend launches without problem, but when I launch my mythtv backend to change a parameter and I try to relaunch my mythtv frontend it tells me that it can not connect to the mythtv backend.
 
Looking around it seems that my MySQL is not more running. Since I am quite a nob with ubuntu, how I can repair this issue?
How to launch the MySQL manually (or define it to be launched after the mythtvbackend setup)?
 
Thanks in advance

---

