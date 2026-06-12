---
title: "Mythbuntu in two hard drives"
date: 2011-03-02
forum: Mythbuntu
---

### Post by macaronij on 2011-03-02
Hi,
(first of all, sorry for my english)

I always used mythbuntu in 1 hard drive, so i just installed very easy
Now i have two hard drives, and i want to make a fresh install
I want to install the root, home, etc in one drive and all the recordings and videos in the second drive
**I WANT TO DO THIS SO WHEN I WANT TO UPGRADE OR FORMAT I CAN EASILY BACKUP THE RECORDINGS**. So please have that in mind for the solution of the problem.
How i have to set the mount points in  the instalation?
i have to put the /var/lib/mythtv in the second disk?
how i manage the swap?

Thanks for the info!!!

---

### Post by Vi3tHoneyX on 2011-03-02
[COLOR=DarkRed]You really don't even have to reinstall. 

You can just format the second drive that doesn't contain the OS and set Mythbuntu to store the data on that drive instead of the other one. There should be a setting in the MythTV backend configuration...

**Edit: you might have to manually copy the old recordings over to the new location**
[/COLOR]

---

### Post by macaronij on 2011-03-02
i really want to make a fresh install, coz i m having troubles whit the video drivers (i just mess the ubuntu drivers and prefer to re-install)
the question is how i manage the mount points
tx!!

---

### Post by LowSky on 2011-03-02
install ubuntu then create folders on the new harddrive for video storage... then on mythtv backend go to storage groups and change the locations to the second drive.

make sure the new folders are part of the mythtv group so recordings can be done correctly.

---

### Post by ijumpship on 2011-03-03
just follow these instruction to install your new drive

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

create the relevant folders videos,music,fanarts etc.

if you copy these from /var/lib/mythtv make sure they have the appropriate permissions

then go to Systems->Mythbuntu BE setup-> storage directories and change them to the new folders you create on the new drive.

I normally do not put my home folder on the other drive since it create so much headache to link the configuration files when I install New software.
After all only configuration files will be in this home directories

I implement this approach to keep all my user files on one drive and the configuration on the other for two reason

1. For Easier backup
2. For when something goes wrong or I want to experiment with an upgrade

Oops, to tell mythbuntu where to find music folders,go to the frontend utilites/setup media settings

---

### Post by macaronij on 2011-03-03
if i copy the old recordings in the second drive, then format the first drive, can i keep my recordings?
i guess i have to follow the backup/restore instructions [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) ?
i have to do the backup before or afther i copy the files to the new drive?

---

### Post by ijumpship on 2011-03-08
Take the tablet (pill) as prescribed in the wiki.

but it make sense to backup before ! [B]"ain't it"
[/B]
tell us if its ok now.

---

