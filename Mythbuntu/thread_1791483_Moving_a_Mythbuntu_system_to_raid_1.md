---
title: "Moving a Mythbuntu system to raid 1"
date: 2011-06-26
forum: Mythbuntu
---

### Post by itlarson on 2011-06-26
This is my follow up to my [previous post]("http://ubuntuforums.org/showthread.php?t=1784814") about installing Mythbuntu on a raid 1.  Since I got it to work this time, I thought I would post How I did it.  Hopefully someone will find this usefull, or at least interesting.

 The way I ended up setting this up is by dividing each of my hard drives into three partitions. Three pairs of partitions were then made into three raid 1 devices.  The partitions which make up each raid device must, of course be the same size, and on different drives.    These devices were then used as root home, and swap.  Once the raid devices were set up, the live CD was used to install Mythbuntu onto these devices, with a few extra steps post-install.  Here's a step by step guide on how I did this, including moving my old system onto the new drives.  

 

-Step one is to backup the mythtv database.  How to do this is detained in this [wiki]("http://www.mythtv.org/wiki/Database_Backup_and_Restore"). Be sure to get the database password from the "general" section of mythfrontend settings.

-I also made copies of /etc/fstab, /etc/X11/xorg.conf, and /etc/hosts, since I have some special settings in them.  This may not be necessary for a more basic system.  Copy these onto a thumb drive with the database.

-Now you can shut the system down.  Unplug the old drives, and plug in the new ones.

-Because My new disks have 4k sectors, I wanted to partition them using the Latest version of Gparted.  Fortunately the Gparted developers make a live CD just for this purpose.  If you have 4k sectors, boot from the Gparted disk, and use the version of Gparted it includes.  If not, the version of Gparted included on the live CD will be fine.  Partition both drives identically.  In my case this was 6g for home, 2g for swap, and the rest for home.  The partitions can be left unformatted.  Save the new partition table, and close Gparted.  If you used the Gparted disk reboot, swapping the Mythbuntu disk for the Gparted one.

-With the system now booted from the Mythbuntu live CD, install the raid driver mdadm.  The command is "sudo apt-get install mdadm".  This is a temporary instalation, lasting only untill your next reboot.

-Now you can build the raid arrays:
  mdadm --create /dev/md1 --verbose --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
  mdadm --create /dev/md2 --verbose --level=1 --raid-devices=2 /dev/sda2 /dev/sdb2
  mdadm --create /dev/md3 --verbose --level=1 --raid-devices=2 /dev/sda3 /dev/sdb3
These commands work as follows:
   --create is creating the array /dev/mdX
   --verbose gives you better idea what's going on in case you have a problem
   --level=1 sets RAID 1
   --raid-devices=2 is the number of devices we want in the array
   /dev/sdaX /dev/sdbX are the devices members of the created array

-Now you need to wait while the raid arrays are built.  For 2tb drives this takes 5-6 hours.  To monitor the process use the command "watch -n0.2 cat /proc/mdstat".  Output looks something like this:
Personalities : [raid1]
md1 : active raid1 sdb1[1] sda1[0]
1953514432 blocks [2/2] [UU]
[====>................] resync = 21.7% (424602304/1953514432) finish=198.5min speed=128317K/sec
unused devices: <none>

-Now you can install Mythbuntu.  The first part of this process is as usual.  When you get to the "prepare disk space" screen, choose "specify partitions manually".  The raid devices /dev/md1, /dev/md2, and /dev/md3 will appear in the partitioning tool.  Each of these will have "free space" underneath it. You can right click on "free space", and create a partition there.  They will be named in the format "/dev/mdXpY" where X is the raid device number, and Y is the number of the partition on that device.  In my experience it is necessary to create only one partition per raid device, using the entire device.  The first time I tried to install on raid, I made a single large raid device, then tried to divide it into three partitions.  Unfortunately the partitioning tool was unable to create the partitions correctly, and the install failed.  So your partitions will end up being named /dev/md1p1, /md2p1, and /md3p1.  Format two of these as ext4, for / and /home, and use the other one as swap.  

-Now you can proceed with the install in the usual way.  But when you finish, be sure to select "continue testing".  

-Before you reboot, it it is necessary to install mdadm permanently on the newly installed system.  because your new root directory is now on a raid device, you can't boot without this driver.  Here is the procedure which allows you to install on the new system without booting it first:
  sudo mount /dev/md1p1 /target/
  sudo mount /dev/md3p1 /target/home
  sudo mount --bind /dev/ /target/dev/
  sudo mount --bind /sys/ /target/sys/
  sudo mount --bind /proc/ /target/proc/
  sudo chroot /target
These commands mount what will be your new file system, and binds the dev, sys and proc systems the live CD created to them.  Then the chroot command makes all this into the acting file system.  Anything you install will now be present when you reboot.  Install mdadm:
  sudo apt-get update
  sudo apt-get install mdadm

-Now you need to update the boot-loader, so both drives will be bootable:
  sudo grub-install /dev/sda
  sudo  grub-install /dev/sdb

-Now you can reboot.  If everything works as it should, shut down the system, and unplug one of the drives.  when you reboot, you will get a message about running in "degraded mode".  Ignore this and boot anyway.  The system should run normally using only one drive.  Shut down again, and try it with the other drive unplugged.  

-Move the data off your old drives.  I was having boot order issues when I tried to boot with both the old and new drives plugged in.  What I ended up doing is booting off the new drives, then hot-plugging the old drives.  You can do this with sata drives.  You will probably have to mount the old drive partitions manually:
  sudo mount /dev/sdX /any-empty-directory

-Restore the database per the [wiki]("http://www.mythtv.org/wiki/Database_Backup_and_Restore").  Hopefully this will be as simple as:
  echo "DBBackupDirectory=/home/USERNAME/BACKUP_DIRECTORY" > ~/.mythtv/backuprc
  mythconverg_restore.pl --drop_database --create_database --filename DATABASE_BACKUP.sql.gz
where DATABASE_BACKUP is in the path.  I had to change the database password to get the front-end to connect to the back-end, but I may have copied the password incorrectly. 

I have found this set-up to run well.  The first couple times I booted, Mythbuntu wanted to run hard-drive checks, but this seems to have cleared up.  The system seems more responsive than before, which I assume is from the faster read speeds of raid 1.  This took a bit of work to figure out, since much of the information on the web about Linux raid isn't up to date for grub 2.  Without [this blog]("http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html") I couldn't have figured it out.  The extra speed, and of course the redundancy factor, make this project well worth the effort. 

Does anyone know if grub 2 allows booting off of raid 5?  I would be curious to know, Even though raid 1 worked best in my situation.

Also, is there anyone besides me who thinks raid set-up should be included in the installer?  It seems like it wouldn't take much to add it to the manual partitioning tool.  With hard-drives as cheap as they are, it seems like a lot of people might like to use raid if set-up was a bit easier.

---

### Post by chipppy on 2011-10-16
Good Morning

Here is the thread I used when I setup a 8000GB RAID5 system with Xubuntu then installed Myth overtop of it.

[http://ubuntuforums.org/showthread.php?t=1764036]("http://ubuntuforums.org/showthread.php?t=1764036")

A few lessons in there but it all worked out fine in the end.  Used the alt install LiveCD.  which is pretty easy except the little traps mentioned in the thread

Cheers
Chipppy

---

