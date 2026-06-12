---
title: "Myth 8.04 Hardy boot errors"
date: 2009-01-02
forum: Mythbuntu
---

### Post by zf3636 on 2009-01-02
Hi i recently added a second drive to use as recordings I have been experiencing problems with mounting the new drive I typed this command sudo mount -t ext3 /dev/sdb1/media /storage in the Terminal and now when I boot up myth will not boot I know have a fchk error press CONTROL D to exit when i do this it then boots up to mythtv, and know new my drive shows as /dev/sda1/media/storage, my drive with the myth O/S installed is dev/sda1 is there a way to undo this change thx.

---

### Post by klc5555 on 2009-01-02
> **zf3636 said:**
> Hi i recently added a second drive to use as recordings I have been experiencing problems with mounting the new drive I typed this command sudo mount -t ext3 /dev/sdb1/media /storage in the Terminal and now when I boot up myth will not boot I know have a fchk error press CONTROL D to exit when i do this it then boots up to mythtv, and know new my drive shows as /dev/sda1/media/storage, my drive with the myth O/S installed is dev/sda1 is there a way to undo this change thx.

Did you properly edit the /etc/fstab file with the correct mount points for the new drive? Just mounting a drive to a mount point by using the sudo mount command does not do anything that persists past the next bootup, if the fstab has not been properly edited.

Are both drives SATA drives, with your boot drive plugged into the first SATA channel on the MB and the second on the second channel (not the reverse)? Is the system using all IDE drives, in which case you've needed to get the channel + master/slave business in the right order? Or is the machine a mixed EIDE/SATA, in which case I have no idea how the OS wants to order the drives, since Ubuntu has ditched the sensible hda, hdb, hdc, hdd naming convention for IDE drives. 

In short, are you sure the machine (bios and/or OS)doesn't think that your storage drive is now sda1 and your OS drive sdb1?

There's also been a bootup glitch (a couple of scripts out of order in the init.d) since at least 7.10, whereby after a cold boot, the machine tries to check the second or subsequent(SATA) drive before it adds it; the check of course fails and you have to exit/kill the single-user prompt whereupon Mythbuntu completes booting up without the second drive. But in this case, a warm restart (ctrl-alt-bckspace followed by ctrl-alt-del) usually fixes everything. Until the next cold boot. 

Just some things to look at.

Good luck!:)

---

### Post by zf3636 on 2009-01-02
Hi I will try the options listed in your post,I have a master IDE DRIVE which has the O/S installed on sda1, and a sata drive as dev/sdb1 and my fstab has been edited to mount the second drive as /dev/sdb1/media/storage defaults 0 2.I am thinking of a reinstal and I would like to know is thier a tutorial guide on how to configure the second hard drive to use within mythtv for my tv recordings.

---

### Post by klc5555 on 2009-01-02
> **zf3636 said:**
> Hi I will try the options listed in your post,I have a master IDE DRIVE which has the O/S installed on sda1, and a sata drive as dev/sdb1 and my fstab has been edited to mount the second drive as /dev/sdb1/media/storage defaults 0 2.I am thinking of a reinstal and I would like to know is thier a tutorial guide on how to configure the second hard drive to use within mythtv for my tv recordings.

I don't know whether such a tutorial exists.

But the steps that are to be taken to add a second drive are quite straightforward, and are basically as follows:

1)After the drive sdb has been physically added, boot the machine, making sure along the way that the bios properly detects the drive in the hardware setup. 
2)Open a terminal and sudo fdisk sdb to add your single primary partition (no. "1") of type 83 (Linux) that takes up essentially the entire drive (that is, it will be "sdb1"). 
3)Format this new partition sdb1 with mkfs, that is: sudo mkfs -t ext3 /dev/sdb1  Some people prefer xfs filesystem for storage, so that you will have sudo mkfs -t xfs /dev/sdb1

4)Make your directory structure under your root filesystem for this new partition to eventually have for its mountpoint, e.g. sudo mkdir  /media then sudo mkdir /media/storage     Now sudo mount /dev/sdb1  /media/storage. Your new sdb1 partition should be accessible in the filesystem as /media/storage. You can test this by sudo copying some file to /media/storage, just to test that it works. I say copy this test file with root permissions, because mythtv (and your regular user) can't use /media/storage yet because the owner, groups, and permissions are wrong.

5)So now sudo chown mythtv /media/storage  sudo chgrp mythtv /media/storage and chmod 775 /media/storage (or chmod 777 /media/storage Some prefer the wide-open setting)

6) Run the backend setup to add /media/storage to your default storage group. Test it by recording something, or moving an existing recording to /media/storage to see whether it functions OK. 

7) If /media/storage functions OK, make the mountpoint permanent by editing fstab. The added line for your sdb1 partition should look pretty much like this:

/dev/sdb1       /media/storage    ext3      defaults       0   2

(Be sure to put the spaces in where they are needed ==the forum editing software here makes them hard to see.)

If, instead, you decide to go xfs (probably not worth bothering about) the line would be:


/dev/sdb1       /media/storage    xfs       defaults       0    2

8 ) And, finally, warm reboot to make sure the whole mess still works afterward.


I've noticed on some mixed ide/sata systems that grub occasionally gets really confused  if the 1st drive/boot drive is sata while the second (or subsequent) drive is ide. Grub's drive nomenclature gets in the way. In these rare cases, the machine has had to be booted from a boot CD and the menu.lst file edited by hand. But on your system the 1st drive and boot drive is the IDE one, so this shouldn't be an issue for you.

Good luck! :)

---

