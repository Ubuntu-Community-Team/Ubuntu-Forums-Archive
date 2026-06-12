---
title: "Partition Question"
date: 2014-03-07
forum: Mythbuntu
---

### Post by jim_collins2 on 2014-03-07
I am doing a new install of mythbuntu.  I have a 4TB drive.  I am a newbie on Linux, but was able to get Gparted to load and I think it is pretty straight forward (I used the myth CD to boot and get Gparted turned on).  My questions are what names and partition sizes should I use and will they be overwritten when I install myth onto the hard drive.  I'm sorry, but I will need very detailed instructions as you can assume I know nothing.  I am going to use the entire drive for mythbuntu.  I may copy movies into the video section, but not sure if they need a partition.  If they do how do I access them after the myth install?  Hope I have been clear in my questions.  I did try to look for this and found that I should probably have a swap partition 2X my RAM so 4GB???  Thanks in advance for all help.

---

### Post by bcschmerker on 2014-03-07
I prefer multiple smaller hard drives myself (each on its own SATA port), but I use a similar approach.  In addition to the Root-Directory Partition (/) and Swap Partition, options include a Users partition (/home), a Variables partition (/var), and a Temporary Files partition (/tmp); an Optional-Programs partition (/opt) is used on some installations, and a User-Programs partition (/usr) was once common practice but no longer recommended due to the heavy use of User Superbinaries (located in /usr/sbin) during the startup process.  The video section referred to your post would most likely be a subdirectory of your User subdirectory (e.g., /home/[color=orange]yourusername[/color]/Videos); in practice current LinUX distros based on the Debian® prepartitioning format will have several video subsections, depending on the number of User Accounts on your rig.

I would recommend putting the Users Partition (/home) on its own hard drive as a hedge against the occasional root-partition crash, as it's not easy to salvage user documents from a hard drive with major damage to media or electronics.

---

### Post by itlarson2 on 2014-03-08
Having everything on one large drive works just fine.  You can put the root partition on a SSD for more speed, but this isn't necessary by any means.  

Ubuntu installs in a single partition by default, but I don't recommend this- even for a desktop system.   Anytime you reinstall, Linux needs to format the root partition, and with this layout your data is IN the root partition.  This means you need to back up the entire drive before reinstalling.  Instead I recommend you make a 20gb root partition, a swap partition the size of your ram,  and the rest of your drive a home partition.  Adding additional partitions was done on early Linux systems, but there is no need for this, it just wastes  space. Volume lables for the partitions aren't needed by Linux, but may be nice for your own use.

You can format the drive from Gparted if you want, but the Ubuntu installer can do it as well.  Either way you need to choose the custom partitioning option in the installer.  I think what you click on is literally called "something else".  Once your in there, it's pretty intuitive how to partition the drive,  and assign the partitions to the right mount points- "/" for root, and "/home" for home.  You should format both of these for a new install, but for a reinstall be sure not to format /home.  One potential pitfall with this layout is that the default storage location for Mythtv recordings isn't in the home directory, so don't forget to change all the storage groups so the point to somewhere in /home.  Failure to do so will result in a full root partition, which causes all kinds of problems.  

As for crashing hard drives- just install a second one.  You can use rsync and cron to keep a full backup of your home partition on this drive.  Even if you don't have a second hard drive, you should make daily backups of your Mythv database, since it is needed for a reinstall.  Again, you can use cron to automate this.  You can find information on how to backup and restore your database here: [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).  For how to use cron and rsync, just google for tutorials.

---

### Post by itlarson2 on 2014-03-08
A few more things after rereading your post.  I think I was assuming too much knowledge in retrospect.

-First.  Other than the partitioning part I talked about installing Mythbuntu  is just a matter of following the instructions the installer gives you and answering it's questions.  that's the easy part.

-Second: you will need an account with [Schedules Direct]("http://www.schedulesdirect.org/") for schedule information. Go set this up while the system is installing.  It costs $25/year.  

-After you reboot, if Mythbuntu wants to install any drivers, let it.  It will need the password you gave during the install.  

-The more complicated part is setting up Mythtv.  The tool for that is in the System menu under "Administration->MythTV Backend Setup".  This will allow you to set up your tuners, scan for channels,  and setup storage groups for videos and recordings.  This is to involved for me to describe, so Google for a tutorial, or find a walkthrough on youtube.  I recomend you use Google's search tools to filter out old results.

-You can put your videos in any directory you want.  Just set the "videos" storage group to point at the directory with the videos, and you will be able to access them from Mythtv.

-Get everything running before you worry about the database backup, or backups in general.  It's not critical until you have a bunch of recordings.

That's all for now.  I'll try to keep an eye on this thread if you have more questions.

---

### Post by jim_collins2 on 2014-03-10
Thank you for your input.  I guess the main thing I need to focus on is the changing of recordings to be in /home.  I had previously used myth and yes, the setup after install is quite intricate.  I am subscribed to schedules direct.  I tried to install a while back and got an error (I am paraphrasing as I did not write it down in frustration) out of disk boot grub.  Just trying to make sure that does not happen again.  If I partition the drive will the install leave it as I set it in Gparted or will the install overwrite my selections?  Thanks again for the input.

---

### Post by oldfred on 2014-03-10
If you partition in advance, you have to use Something Else and choose (change) which  partition is /, /home etc and its format.

If you format in advance you need an efi partition if booting in UEFI mode, or a 1 or 2MB unformatted partition with the bios_grub flag for grub to install correctly with gpt partitioning. With your large drive you need to use gpt.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....



Screen shots from a standard install using Something else.

---

### Post by aelfric55 on 2014-03-10
> **jim_collins2 said:**
> ...I guess the main thing I need to focus on is the changing of recordings to be in /home.  I had previously used myth and yes, the setup after install is quite intricate.  I am subscribed to schedules direct.  I tried to install a while back and got an error (I am paraphrasing as I did not write it down in frustration) out of disk boot grub.  Just trying to make sure that does not happen again.  If I partition the drive will the install leave it as I set it in Gparted or will the install overwrite my selections?  Thanks again for the input.

You should probably leave the recordings directories under /var/lib/mythtv, where they would be set up by default anyway. Putting them under /home (or worse still under /home/<your user account>) is almost guaranteed to get you stuck for a while troubleshooting weird permissions/group/path issues as root, mythtv, and your user all try to access various aspects of the recordings, database, and hardware. 

I've come to take a more extreme position with mythtv over the last 6 or 7 years: I never put everything on a single drive, multiple partitions or not. On a mythtv system I always put the whole OS on a small, separate drive (say 60GB to 180GB), and use one, two, or several large SATA drives (1TB to 4TB), each formatted into single large partitions and each mounted somwhere under /var/lib/mythtv/ for recordings storage. The daily MySQL backup routine backs up a copy of the database to each of the storage drives on the master backend, because having some/most recordings survive a major crash without a copy of the db surviving would be fairly useless.

---

### Post by jim_collins2 on 2014-03-10
I have a 1 TB drive that I can put into that machine.  Should I just format that drive and get it completely set up and then add the second 4TB drive afterwards?  I never heard of the 1MB or 2MB unformatted partition.  That could be my problem as is.  I used to do a lot more hardware modifications and was more familiar with windows and older drives that were a master and slave.  how do I get the system to boot from a specific drive (choose one over the other) if not master/slave??

---

### Post by oldfred on 2014-03-10
New systems are totally controlled by BIOS. Even the somewhat newer PATA/IDE with cable select let you use BIOS to choose which IDE drive. 
New SATA drives have no on drive settings and only BIOS can change which is used to boot. Or very new system it now is UEFI which replaces BIOS.

Because drive is 4TB and MBR has a hard max of 2TB because it is 35 years old and when designed MB was large, GB very large and TB unheard of in PCs.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

If you have an old system, its BIOS may not see very large drive correctly.

---

### Post by itlarson2 on 2014-03-10
I still don't see the point of putting root on its own drive.  I have run Mythtv and other linux systems with root on a partition for years.  As for recording storage, I use a directory in /home, but outside my user home directory.  I just make sure everything in storage groups points there instead of the default, except the videos group, which points to ~/Videos.  I also think I changed permissions to allow anyone to write to that directory years ago, since there can be problems with user ID's after a reinstall.  If I was to redo everything, I think I might just make the default location into a pointer to the actual storage directory.  This would prevent any problems as long as you made sure the link had the same owner and permissions as the original directory.

---

### Post by jim_collins2 on 2014-03-10
My computer recognizes the 4TB hard drive without problems (well I am assuming the out of disk boot grub problem was not a hard drive size problem).  I assume it was the fact that I did not leave some portion of the HD unallocated?  I am going to try to have the 4TB drive as the only drive and set recordings to the default so I can get up and running.  Thanks everyone for the input.  I should get to this tonight.

---

### Post by oldfred on 2014-03-10
You can get the out of disk type issue if you use default install of one / (root). I do not think they planned on that with TB size drives. Some BIOS just do not boot from that large of a partition.

Better to have a smaller /  or 20 or 25GB near beginning of drive and use rest of drive as /home or /mnt/data for all your data.

---

### Post by jim_collins2 on 2014-03-15
Well I finally got some time to work on the system.  I definitely made some sort of colossal error.  I partitioned the drive using the "do something different" in the install.  I had a 20GB root, 2GB swap, and left some unformatted.  The install seemed to go smoothly.  Got to the point where it says to remove the installation disk and restart.  I did that and got the following:

Error: unknown filesystem.
grub rescue>

I am back to frustration.  I have used this exact drive in the past for this and it worked.  I do not remember doing anything different, but apparently I did.  Does any of this make sense to anyone????

---

### Post by oldfred on 2014-03-16
Something with grub did not install correctly.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

You may just need to do this if grub.cfg is ok.

 grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

---

