---
title: "MySQL not setup during mythbuntu installation"
date: 2008-01-22
forum: Mythbuntu
---

### Post by paulwheeler on 2008-01-22
I have tried to install MythTV using the gutsy ubuntu and the gutsy mythbuntu iso downloads. Unfortunately, I have found that the MySQL database is not setup (mythtv user, mythconverg database) during the installation and several trips through all the various screens. Running fillmythdatabase has no effect either.

I manually created the user and database during one of the many tries, but could only get black and white tv with no sound. [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

Is there a complete list of steps needed to install mythtv and have it fully operational? If so, I have not found such a list.

I assumed that the mythbuntu iso would do EVERYTHING necessary to get a fully functional program. Evidently I was wrong, or am missing some major installation componenet somewhere.

Can anyone please help me? [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by tgm4883 on 2008-01-22
Did you verify the integrity of your CD?  are you doing an advanced or standard install?  Which CD are you using?

---

### Post by Sdrabor on 2009-01-24
I'm having a very similar issue.  I am using the Mythbuntu 8.10 disk, and I did verify the cd before running the install.  When I go through the MythTV Setup for the MySQL portion, it is not able to connect for some reason and create the database.  If I log into MySQL manually and create the database, username, and password, and assign all privileges to that database, it still is unable to connect... 

any ideas?  I'm a bit stuck until I'm able to get this running ](*,)

---

### Post by stevedaniels on 2009-01-25
I had this problem as well. In the end I manually setup the database tables using the mc.sql script. I also manually created the mythtv database user with the password contained in /etc/mythtv/mysql.txt I did that using the mysql-admin util, remembering to assign all privileges to the mythconverg database/catalog.

Good luck!

Steve Daniels
(I'm just stating to battle with "Build Image" not working!)

---

