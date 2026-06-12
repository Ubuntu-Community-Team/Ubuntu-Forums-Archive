---
title: "Migrating from 0.22 to 0.23"
date: 2010-04-29
forum: Mythbuntu
---

### Post by Slate8 on 2010-04-29
Hi All. 

Has anyone found a good guide for migrating from 0.22 (Mythbuntu 9.10) to 0.23 (Mythbuntu 10.04)? I'm hoping I can just do a mysqldump from one to the other assuming the schema hasn't changed this time round?

Many thanks.

---

### Post by jbman on 2010-04-29
I went from 8.04 to 10.04 Beta 2 just from and update -d.

when I loaded mythtv 0.23 for the first time it asked would i like to do the database update, it then did a backup and updated.

This was from 0.21-fixes to 0.23-fixes

---

### Post by novellahub on 2010-04-29
On my past few upgrades I have been using this guide:

[http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

I have been using it since Mythtv 0.20 on both Knoppmyth and Mythbuntu systems.  The only difference from the directions given, I use the root user instead of mythtv.

This time around I am going to give the update manager a try and see how it goes.  I am going to back up my key files first (lircrc, xorg.conf, asound.conf, etc.)to a flash drive and then do the upgrade.

---

### Post by Slate8 on 2010-04-29
Thanks for the link. I've never been able to get a dist update to go smoothly and am planning a clean install anyway.

I have read through the migration guide but it only seems to cover backing up and restoring the recordings data. I was hoping to do a complete dump so that tuners, channels, storage groups, video filetypes data etc is all retained.

Does anyone know if this is possible or am I hoping for too much? I'd really like to avoid setting everything up again settings wise if I can help it.

Thanks again :smile:

---

### Post by Al_Vampyre on 2010-04-29
[This]("http://www.mythbuntu.org/Upgrading") should help

---

### Post by dannyboy79 on 2010-04-29
i would just go with a dist-upgrade. i have upgraded from jaunty to karmic, and now to lucid and all went fine. backup just in case. if you really want to dump your database and do a fresh install see the above guide.

---

### Post by Slate8 on 2010-04-29
Thanks so much, the mythbuntu.org link has just the info I was looking for!

I decided I might as will try a dist upgrade anyway, got nothing to loose so will backup first and give it a bash. 

Looking forward to the new release. Thanks for all the help.

---

### Post by Slate8 on 2010-04-30
Just wanted to update this thread with how I got on...

I took a backup of my DB. Then did an update via the Update Manager. Rebooted, then did the dist upgrade via the Update Manager. All went well more or less. 

I had one minor error about network manager not being able up upgrade during the upgrade process.

Upon reboot the device ids for my various internal hard drives had changed, and kept changing on subsequent reboots. To solve this I changed my fstab to use the UUID rather than device id.

Everything else is perfect and all my settings and recording etc have been retained. I am now using the Arclight theme with custom backgrounds and it looks most shiny :)

Thanks for the help and nudge to try a dist upgrade.

---

### Post by bgiannes on 2010-04-30
okay, so ubuntu 10.04 LTS does ship with mythtv 0.23 in the repo right
and mythubuntu ships with 0.23?


I have ubuntu 9.10 with mythtv back-end (raid 5 3T for video and recordings) and front-end on main LCDTV, and one wireless mythubuntu 9.10.

you using raid?

if you do a start over install; the best way, (very clean) to backup the DB is to use webmin and use there mysql backup tools. then do the install, then use webmin again to restore the DB.  
As i don't like trying to find the correct version of the mythtv DB backup script.

---

### Post by bgiannes on 2010-05-05
well to answer my own Questions, the current mythtv 0.23 in the lucid repo seems to be a RC1 or 2?

The raid/mdadm didn't upgrade correctly and i had to manual reinstall it.

The mythfrontend will not load and crashs on startup.  luck the backend seems to be working just fine.

I then tryed doing a fresh install but have the same mythfrontend bug.  

But my stand-alone frontend does work.  So i can still watch tv from there.

---

### Post by iamlindoro on 2010-05-05
> **bgiannes said:**
> I then tryed doing a fresh install but have the same mythfrontend bug.

Since you don't include logs or debug output, it's difficult to know for sure, but this is almost certainly a bug that has been fixed.  Install the auto-builds repository and upgrade to current .23-fixes, voila.  ;)

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by tgm4883 on 2010-05-05
> **bgiannes said:**
> well to answer my own Questions, the current mythtv 0.23 in the lucid repo seems to be a RC1 or 2?

The raid/mdadm didn't upgrade correctly and i had to manual reinstall it.

The mythfrontend will not load and crashs on startup.  luck the backend seems to be working just fine.

I then tryed doing a fresh install but have the same mythfrontend bug.  

But my stand-alone frontend does work.  So i can still watch tv from there.

I would upgrade to auto-builds, as it contains a newer version that what is in the repos

---

### Post by bgiannes on 2010-05-05
thanks, i ran the auto-builds and the system is backup and running, ps i did ID the bugs i was having and saw they are "fixed", but i didn't understand the fixes go to the auto-builds first, then i assume they are past to the standard lucid repo.

Question:
once the stable 0.23 version is released, and i turn off the auto-build repo how does that work, how can i wean myself off it....

---

### Post by iamlindoro on 2010-05-05
You don't.  There is no condition under which you wouldn't want to be running what's in the auto-builds.  The only things that go there are the fixes that get backported to .23, you are not running a development version.  You are running .23-fixes and the only updates you will see are bugfixes.  This is a good thing.  :)

---

### Post by SeanOB on 2010-10-10
I'm debating updating...
I'm way back at 0.21 (mythbuntu 9.04).  Its been so rock stable -- but I like the flashy new themes...

I have two boot partitions -- current stable and the next release.  This buys me time to get the next release up and running -- since I default boot to the known good release.  The downside is that every install is a fresh install - I can't use the upgrade utilities.

Recordings etc are on a completely different drive / partition.

In the past I've just moved the database (and other config files) from the old release to the new.  But moving from 0.21 to 0.23 is going to make this impossible.

I really only want to keep:
- existing recordings
- recording history -- to prevent duplicates
- channels
- recording schedule
(I guess that's everything!)

Is there a script that can migrate my database?  Or just a sequence of mysql steps to export / import the tables that I need?

Thanks!

---

### Post by tgm4883 on 2010-10-10
> **SeanOB said:**
> I'm debating updating...
I'm way back at 0.21 (mythbuntu 9.04).  Its been so rock stable -- but I like the flashy new themes...

I have two boot partitions -- current stable and the next release.  This buys me time to get the next release up and running -- since I default boot to the known good release.  The downside is that every install is a fresh install - I can't use the upgrade utilities.

Recordings etc are on a completely different drive / partition.

In the past I've just moved the database (and other config files) from the old release to the new.  But moving from 0.21 to 0.23 is going to make this impossible.

I really only want to keep:
- existing recordings
- recording history -- to prevent duplicates
- channels
- recording schedule
(I guess that's everything!)

Is there a script that can migrate my database?  Or just a sequence of mysql steps to export / import the tables that I need?

Thanks!

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

