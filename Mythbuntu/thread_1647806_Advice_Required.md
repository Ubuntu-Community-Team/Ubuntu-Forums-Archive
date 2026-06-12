---
title: "Advice Required"
date: 2010-12-17
forum: Mythbuntu
---

### Post by uncle hammy on 2010-12-17
I currently have 3 drives in my MyhtTV backend (actually, there's a 4th, but it's all for storage other than MythTV).  

sda = 500GB drive...
partition 1 = 10GB for /
partition 2 = 2.5GB for swap
partition 3 = remainder for recordings

sdb = 320GB drive
partition 1 = recordings

sdc = 500GB drive
partition 1 = recordings

All partitions are ext4.

I am going to purchase a 40GB SSD drive and a 1TB drive.  I want to move the recordings from sda,partition 3 and sdb to the new 1tb drive, then remove them from the system.

I would then like to move the swap partition and the / partition from sda to the SSD and use it as my "system" drive.  I'd like to have the swap stay the same size, and expand the / partition to fill the remaining space on the SSD drive.

The part I am not sure how to proceed on is the new system drive.  Can anyone offer me advice on how to move those 2 partitions to the new drive?  Preferably in a manner that essentially lets me just move it and go after it's done.  Obviously, I know I can do a new install, but I was kind of hoping to move it over.  Maybe the fresh install is the easiest?

---

### Post by uncle hammy on 2010-12-18
Well, FWIW, I got it done and it worked out fairly well. In case anyone else is looking someday, here's what I did (i'm sure there will be plenty of gurus out there will say "you did WHAT?" :))....

1. Moved all all files from the 320GB drive to my files storage drive that had enough room to hold them (my MOBO only has 4 SATA connections, so I had to work with this).
2. Removed the 320GB and replaced it with the new 1TB drive.  Started up, ignored the "this drive is now missing and can't be mounted" errors.
3. Installed GParted, created one ext4 partition on the new drive.  Once that was done, got the UUID from GParted's info screen and modified fstab to mount that to the directory the old 320GB drive was being mounted to.
4. Moved all the files from step one to the new 1TB drive, and all the recording files from the 500GB drive that will be going shortly to the new 1TB drive.
5. Cleaned up fstab match the new layout.

OK that takes care of my recordingg, on to the new system drive.....

1. Followed the instructions [here](http://ubuntuforums.org/showthread.php?t=35087) to use tar to backup my system, I also added excludes for all my mythtv storage directories.  However, I backed it up to one of the other drives instead of / because that drive is about to come out of the machine.
2. Removed the 500GB system/recordings drive and replaced it with the new SSD.
3. Rather than mess around with issues with grub and fstab that would result from cloning the drive, I simply did a fresh install on the new 40GB drive, making sure to mount but not format my mythtv drives during the install.  Once done, I now have a shiny new grub and fstab, so I simply copied fstab to one of the other drives for safe keeping.
4. Continuing with the instructions from 1, I copied my tar backup to root and restored it using the command indicated in the how-to.
5. Step 4 obviously over-wrote my shiny new fstab with the old one from my backup, so I copied the shiny new one back from where I saved it in step 3.
5. sudo update-grub, just to be safe.
6. Reboot, and I am back to where I was, everything seems happy.
7. Clean up my storage groups in mythtv to match the new layout.

I can't say for sure, but I don't think the fresh install / tar backup restore took any longer than cloning the partitions and then farting around with broken grub and fstabs.  If it did, it was negligible, and certainly avoided a lot of headaches.

Hope that helps someone some day.

---

