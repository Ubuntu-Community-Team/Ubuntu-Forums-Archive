---
title: "mythtv woes.."
date: 2009-09-20
forum: Mythbuntu
---

### Post by rp3 on 2009-09-20
Ok first I have Ubuntu on a machine that I have been using for many things, and decided to give MythTv a try, I got a HDHomeRun which looks great, and does exactly what I need OTA stuff with my Terk Ant...

That works fine.

I installed MythTv through Synaptic and it seems I messed something up on the initial mythtv-seutp as now I get the dreaded 'can't log on to db' loop.  I think I forgot a pin or something?  Not sure.

The issue is I can't remove enough to start over, I tried to apt-get -purge mythtv-common etc.. but to no avail.

I remove (Drop) the DB, and I get the question to create the new DB but thats what it does then I can't run mythtv-backend...

Not sure where to start, stop, etc..any help appreciated.  If I could get it back to the install and setup I think I could make it work, I never imagined I could break it this way just not putting in a PIN "0000" or something??

Thanks,

Rp

---

### Post by bsntech on 2009-09-20
Hi rp3,

When you setup MythTV, it should have also installed the MySQL server.

When you were prompted for a root password for the MySQL server, did you leave it blank or enter something?  If you entered something, the MythTV setup wizard would have prompted you for the MySQL root password so the scripts could login and setup the database and create the mythtv user account for regular access.

Your mythtv user name and password are stored in this file:

/etc/mythtv/mysql.txt

Ensure this username and password is the same one that you have listed in myth-backend, otherwise MythTV won't be able to login to the database - therefore causing the error above.

Otherwise, if you set a root password for MySQL and didn't set it during the MythTV setup process, this would also cause the above error.  To fix this, you will need to re-run the setup for MythTV.

sudo dpkg-reconfigure mythtv-common

Here is another web page for you to go through for further assistance:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting")

---

### Post by rp3 on 2009-09-21
> **bsntech said:**
> Hi rp3,

When you setup MythTV, it should have also installed the MySQL server.

When you were prompted for a root password for the MySQL server, did you leave it blank or enter something?  If you entered something, the MythTV setup wizard would have prompted you for the MySQL root password so the scripts could login and setup the database and create the mythtv user account for regular access.

Your mythtv user name and password are stored in this file:

/etc/mythtv/mysql.txt

Ensure this username and password is the same one that you have listed in myth-backend, otherwise MythTV won't be able to login to the database - therefore causing the error above.

Otherwise, if you set a root password for MySQL and didn't set it during the MythTV setup process, this would also cause the above error.  To fix this, you will need to re-run the setup for MythTV.

sudo dpkg-reconfigure mythtv-common

Here is another web page for you to go through for further assistance:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting")

I know I am missing something basic :(

I made sure my user was in the mythtv group.
```
rp@rpzathlon:~$ grep mythtv: /etc/group
mythtv:x:135:rp,root

```

I removed mythtv dirs and got no where.

I set a root pw (Assuming this is my phpMyAdmin pw?)

But when I try to change root mysql pw I get this?

```
rp@rpzathlon:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

Maybe that helps, maybe not, I also noticed where it said to purge MySql possibly but I wouldn't want to do that??  Any more ideas?

Was also trying to cut n paste window but can't figure out how.  What port should mythtv be connecting too?  6543 was in there, I tried 3303 and blank but still get the message like mythtv can't even find the connection?  Maybe an MySql issue?

Kewl, just kept messing with it and now I got mythtv-setup to run, will play with it a bit more, then off to get another client running...

I am sure you will hear from me some more, frustrating thing is I am not 100% sure what I did to fix it.  I think it was a combination of PW and port that got me messed up...

But this is what makes it fun...

---

### Post by rp3 on 2009-09-22
Ok more to the story, isn't there always...

Since I got it running, the backend, and setup my stations, setup the HDHomerun, and downloaded the guide, and icons, etc.. I decided to reboot to make sure it all worked as it should.

First thing, it didn't start automatically, but that was easy to start, no biggie there, then I noticed that the HD light went full on, and HD was going crazy, I thought maybe it was just catching up.  Really no idea what it was doing.  So I thought I would give the frontend a go (all on same box so far) and it started up, then let me know it didn't know where the server was so I had to set that up.  All looked great until I tried to get out of the frontend setup and it just sat there on the black screen.

I waited a bit, then when it still hadn't done anything I killed it.  Went to run 'mythtv-setup' just to make sure that still worked and things were still good and I got the normal window but it stoped after the first three lines or so.  

I just tried to run it again, and I get the looping scenario again :(... but a new error it seems.  'mythtv: could not connect to socket' seems to be the issue this time... I will do a search for this, but it's bed time...

Hmm interesting what it is doing, seems to be taking forever to run, and now that it started the backend up again, the HD light is solid and the DISK monitor is practically solid?  Hmmmmmm

Doing a ```
sudo /etc/init.d/mythtv-backend stop
```

Stops the HD activity and the light goes immediately off?

Hmmm

---

### Post by williammanda on 2009-09-22
If it were me....I would re-install Ubuntu then mythtv control center. You are having possibly some weird outcomes based off of the info you have provided. Not only that you have spent more than triple the time it takes to re-install. Unless you have hardware issues then this route should make sense.
If you choose this route please partition the drive correctly. Use at least 10G for the "/" directory as ext, Equal or double the size of your ram for the "swap" directory and the rest in the "/var" directory as xfs. Also I would format the drive as well.

Also please write down the mysql password and just hit enter when the setup prompts you about mythtv password.

---

### Post by rp3 on 2009-09-22
> **williammanda said:**
> If it were me....I would re-install Ubuntu then mythtv control center. You are having possibly some weird outcomes based off of the info you have provided. Not only that you have spent more than triple the time it takes to re-install. Unless you have hardware issues then this route should make sense.
If you choose this route please partition the drive correctly. Use at least 10G for the "/" directory as ext, Equal or double the size of your ram for the "swap" directory and the rest in the "/var" directory as xfs. Also I would format the drive as well.

Also please write down the mysql password and just hit enter when the setup prompts you about mythtv password.

Not an option, but I will figure it out, seems something is set wrong, I would rather fix (plus thats more fun) then reload, that too often is the answer.  Much more gratification that I fixed it than just reloading and could be right back here... Who knows, I will keep tinkering and let you guys know what I find... ;)

---

