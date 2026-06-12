---
title: "Upgrade path from 7.10 to 8.10 - can I skip 8.04"
date: 2008-10-01
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-10-01
I have a nicely working 7.10 install, and I didn't therefore bother to upgrade to 8.04 when it came out. 

I have just purchased a USB tuner (Asus u3100) that works excellently with Ubuntu 8.04, but not with my Mythbuntu 7.10, so I now need to upgrade (I should upgrade anyway).  I notice, however, that 8.10 is in alpha, so I may wait until it is ready.  

The problem is that I notice this info in the announcement  

"It is very important to note that this release is not compatible with Mythbuntu 7.10 or any other MythTV 0.20.2 based distribution. "

So, does this mean it won't upgrade a 7.10 box, or just that it won't work with, say, a 7.10 backend?  What should my upgrade path be anyway?  Should I go to 8.04 first, then to 8.10, or can I upgrade from 7.10 straight through to 8.10?

---

### Post by modmadmike on 2008-10-01
the Ubuntu release dates are in the version number, thus 8.10 will come out sometime in October of this year so yes you could wait for its not that far away.

---

### Post by modmadmike on 2008-10-01
Sorry didn't read your full post, I guss it would be better to got to 8.04 then 8.10

---

### Post by iponeverything on 2008-10-01
Go to 8.04 first then to 8.10 -- Unless you like bad odds.

---

### Post by ubnewbie2 on 2008-10-01
I see, so the chances of it working seamlessly will be better if I take each step.

So, that begs the question - what are the gotchas invloved in going from 7.10 to 8.04 (or 8.04.1 actually I suppose)?  Will it preserve my existing database and recordings, including my schedules?

---

### Post by laga on 2008-10-02
First step: get a complete backup of your system.

To answer your question: yes, a 7.10 backend won't work with a 8.10 frontend (and vice-versa).

Your existing schedules etc should be preserved.

---

### Post by ozybushwalker on 2008-10-02
I would second the advice to get a complete backup. I upgraded from a working 7.10 system to 8.04 and despite spending many hours trying to work out what was going wrong, was unable to get 8.04 working. I have since done a fresh install of 8.10 Alpha 6 and it works fine.

If I recall correctly, I was not alone in my inability to get 8.04 working, though lots of people seemed to have no trouble with 8.04.

---

### Post by newlinux on 2008-10-02
As far as myth goes (don't know what else you have on your machine) I'd backup your database, recordings, and other myth media and just 8.10, and restore your database, recordings, and other media to the same spots they were in your previous install. For me, I try to keep my recordings  on a different partition, so a new install doesn't affect them. But if you have a lot of other configs with other things on the system you may want to try the upgrade path (7.10-8.04-8.10) if you don't want to recreate them.

---

### Post by ubnewbie2 on 2008-10-02
> **newlinux said:**
> As far as myth goes (don't know what else you have on your machine) I'd backup your database, recordings, and other myth media and just 8.10, and restore your database, recordings, and other media to the same spots they were in your previous install. For me, I try to keep my recordings  on a different partition, so a new install doesn't affect them. But if you have a lot of other configs with other things on the system you may want to try the upgrade path (7.10-8.04-8.10) if you don't want to recreate them.


I have a few things that it would be easier not to have to set up from scratch, so I might try the upgrade path.  If I take a backup, and the upgrade fails, I can always fall back to a clean install.

What is the correct/recommended method to back up and restore the database?

---

### Post by newlinux on 2008-10-02
[http://www.mythtv.org/wiki/index.php/Backup_your_database](http://www.mythtv.org/wiki/index.php/Backup_your_database)

I actually recommend on your new install that you regularly backup your DB. I think mythbuntu-control-centre may have an option to do this automatically, but I just run a nightly cron and keep backups on my fileserver.

---

### Post by ubnewbie2 on 2008-10-02
> **newlinux said:**
> [http://www.mythtv.org/wiki/index.php/Backup_your_database](http://www.mythtv.org/wiki/index.php/Backup_your_database)

I actually recommend on your new install that you regularly backup your DB. I think mythbuntu-control-centre may have an option to do this automatically, but I just run a nightly cron and keep backups on my fileserver.


A very well written wiki page!  Thanks for the link.

---

### Post by ubnewbie2 on 2008-10-05
Thanks to all the help here, I have managed to upgrade my 7.10 install to latest, then upgrade to 8.04, then add my 3rd DVB tuner (the ASUS U3100 USB tuner) and it's all working!!!

All database data was retained (but it was nice to have the backup just in case).  Only one glitch along the way - after I updated my 7.10 to latest updates (some 150 odd updates as I had never updated it before), on the first reboot the X server didn't start (at least all I got was a blank screen at the point that X tried to start.  Luckily a reset/reboot and it came up working second time. All water under the bridge now - I am a very happy Mythbuntu 8.04 user with 3 tuners - and eagerly awaiting 8.10 coming out.

btw: one feature that's new - storage groups, is going to be very useful for me.

---

