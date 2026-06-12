---
title: "Moving recording to a different backend. what tablles do i need to backup in the DB?"
date: 2013-04-29
forum: Mythbuntu
---

### Post by drewdin on 2013-04-29
My Hard drive is 95% full, I just got a new 2TB drive that I want to move my recordings to. I am also going to upgrade from .24 to .25 since I am changing so much. Can anyone provide me with the tables I need to backup so when I move them over to .25 they will work properly?

I checked a few different websites and they all had different tables. From what i have been reading, are these the only ones I need to worry about is that correct? Thanks

oldrecorded
record
recorded
recordedmarkup
recordedprogram
recordedrating
recordedseek

---

### Post by drewdin on 2013-04-29
no one? any one? bueller?

---

### Post by PhilWig on 2013-04-30
Many ways to crack this but:

If you want to end up with a single disk system then set up 0.25 on your 2TB, test it to death for functionality, stability and waf.  Then mount the old disk, copy recordings across.  Do a database backup under 0.24 and copy it to (say) a usb stick, database restore under 0.25.  The database will then be updated to 0.25 format.  Retire the old disk.

However, you might like to consider splitting traffic across 2 disks - root, swap, database on one, /var/lib/mythtv on the other.  I run a 500GB with root, swap and a backup of a subset of recordings.  Also a 2TB with emergency root and swap 
partitions and /var/lib/mythtv.  See autobackup in the wiki.

I'm sure others will have their favoured solutions.

hth
Phil

---

### Post by jksj on 2013-04-30
Just to be clear you have to backup the whole database using:-
  /usr/share/mythtv/mythconverg_backup.pl --verbose
and restore it with
  	 	 	 	     usr/share/mythtv/mythconverg_restore.pl --drop_database --create_database --filename [COLOR=#006400]from backup[/COLOR]
See [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by drewdin on 2013-04-30
last night i moved over the 1TB of data to the 2Tb drive, tonight I plan on moving the disks out. Right now I have the 1TB mounted to /media/mythtv, is that not recommended? should I move it to /var/lib/mythtv as listed above? Thanks

---

### Post by AlecJ on 2013-05-01
Do you only have space for 1 drive then?
I would just add the 2Tb drive and set the path for recording to use it as well as the exsisting.
I have 1 ssd 30GB for the mythbuntu system and 5 drives for the media and recordings etc
They all mount with fstabs at boot, regular backups mean if I lose the system it's only a few min's to retrive everything

---

### Post by drewdin on 2013-05-01
I have two drives also, a 60gb ssd for the OS and a 2tb drive for recordings etc...

I only wanted to move the recordings at first, I did this last night. I have everything mounted in the fstab to /media/mythtv/recordings, etc... I didnt know if that location would be an issue or not, the only issues I had were changing the ownership and permissions on the folders ion the new drive.

I plan on Migrating over to .26, right now im using .24. I only wanted to bring over the recordings, that why I wanted to know only the tables associated with recordings. I'll backup the whole db if I have to but i wanted to start from scratch but keep everything i recorded to this point. Thanks

---

### Post by newlinux on 2013-05-02
Despite what google results might tell you, I'm pretty sure the only reliable way to migrate recordings in recent versions of myth is to copy the whole database, and then if the new machine where the recordings will be placed will have a different name than the current machine with recordings you'll have to update some records in the database.

---

### Post by drewdin on 2013-05-02
I plan on keeping the same names, the old database has been through the mud and i didn't want to bring over any legacy issues if there were any. I guess I will try it both ways and if just the few tables I have listed above do not work then ill just copy over the whole database.

---

### Post by BicyclerBoy on 2013-05-04
You should read & understand the warnings here:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

The partial restore should only be attempted if the (source) DB schema matches installed (current running) version.

---

### Post by drewdin on 2013-05-22
> **BicyclerBoy said:**
> You should read & understand the warnings here:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

The partial restore should only be attempted if the (source) DB schema matches installed (current running) version.


SO if i plan on upgrading to .26, would that be considered a DB schema match? Im guessing it won't but I want to make sure.

---

