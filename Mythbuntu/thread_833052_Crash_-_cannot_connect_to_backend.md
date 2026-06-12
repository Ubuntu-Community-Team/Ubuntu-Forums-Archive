---
title: "Crash - cannot connect to backend"
date: 2008-06-18
forum: Mythbuntu
---

### Post by davidstoll on 2008-06-18
MythBuntu froze up and I finally had to hit the reset button.  When it started back up, the "look/skin/icons" of the front end changed.  It also says "cannot connect to backend" every time I try to click a menu item, I get the same message/error.

I followed some instructions to check the integrity of the mysql database and everything seems fine.

Something obviously got corrupted.  What can I do?

P.S.  I'm a big time linux n00b, so be gentle and baby step me through any suggestions you make.  Thank you for any help you can give!

---

### Post by klc5555 on 2008-06-18
So far as I know, whenever something like this happens after a hard reset, the mythconverg database is corrupted. If so, restoring from a recent backup is the normal remedy. I toast a database about once a month from hard resets after NVidia or cpu thermal lockups, or after power flukies --I find daily backups the one thing that makes mythtv really useable for me.

Lacking a handy backup, I would exit myth to the desktop and run mythtv-setup from a prompt or from the control center to see whether the backend was still set up the way I had left it, or if it needed to be set up from scratch again. In the latter case, I'd set it up as it was set up before, run mythfilldatabase to save the data, and then start the frontend again. If mythconverg was completely corrupted, your recordings data will also be gone, which is the one thing that is hard to replace.

For backing up and restoring mythconverg, including a lifesaving daily backup script, see [http://mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance](http://mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance)

For a reminder on setting up the backend and/or frontend, see [http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend](http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend)

and 

[http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend](http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend)

Good luck!

---

### Post by klc5555 on 2008-06-18
Sorry: the silly post-editing software truncated the links to the manual pages I attempted to list.

They can be found under the general index for the manual at the wiki at [http://mythtv.org/wiki/index.php](http://mythtv.org/wiki/index.php)

All the best.

---

