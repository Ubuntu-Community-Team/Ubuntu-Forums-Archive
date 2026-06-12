---
title: "How to install as third OS"
date: 2008-05-12
forum: Mythbuntu
---

### Post by roundhay on 2008-05-12
i have 4 HDD in my set up, 2 x 500GD storage drives and 2 x 160GB drive to be used for operating systems. I currenbtly have Ubuntu on one drive and XP on the second.

I want to install Mythbuntu onto a partition on the Ubuntu drive. (I want to keep my Ubuntu install)

The current drive layout is:

/dev/sda
  /dev/sda1   ntfs

/dev/sdb
  /dev/sdb    ntfs

/dev/sdc
  /dev/sdc1   ext3
  /dev/sdc5   swap

/dev/sdd
  /dev/sdd1   ntfs

There is plenty of room on the drive but I'm not sure  / confident that I know how to partition the drive and then install  mythbuntu. I have tried to create a partition using gparted but all of the options were graeyed out?

Can I create the partition during the mythbuntu install?

Any pointers / help appreciated

---

### Post by volkswagner on 2008-05-12
Boot into the live CD.  You can use your Ubuntu/mythbuntu live cd.  Go to partition manager.  You will need to know what is your current partition for ubuntu.  If there is not enough free space to  install, shrink your current ubuntu partition.  You can then create a new partition for mythbuntu and format to ext3.  You may also be interested in creating a partition for media, ie /var/lib/mythtv/ for all media or /var/lib/mythtv/recordings for just recorded tv.  You can also create your own directory/mount point such as /mythmedia and change the directories within mythtv.


Edit:  The reason the drives were grayed out.....you would need to unmount them.  You can't unmount your current system, hence the live cd.

---

### Post by roundhay on 2008-05-21
I have followed the instructions above and now have the following drive layout:

/dev/sda
/dev/sda1 ntfs

/dev/sdb
/dev/sdb ntfs

/dev/sdc
/dev/sdc1 ext3
/dev/sdc6 ext3
/dev/sdc5 swap

/dev/sdd
/dev/sdd1 ntfs

I have installed mythbuntu 8.04 onto the /dev/sdc6 partition but I'm not sure I have done it correctly. Can someone let me know what type of 'mount point' I should use? Should it be 'boot'???

The other info I need is how to amend the grub files so that I can boot mythbuntu from grub?

---

### Post by volkswagner on 2008-05-21
Mythbuntu file system you will mount it as /.  You can create symlinks to your media if you like.

Your grub should be installed to your boot drive (most likely windows partition).  This option is under the advanced tab.  It is the last step prior to install.  If you already installed, you can reinstall grub if needed.

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

EDIT:  You can find an "*" at your boot drive with the following command.

sudo fdisk -l

---

### Post by roundhay on 2008-05-21
I have attached the output from sudo fdisk -l

It looks like I have 2 boot partitions, on is the XP partition and one is the Ubuntu partition.

I would rather not get into reinstallation of Grub, I've had loads of problems with this in the past. I'm fairly sure you can add the mythbuntu o/s to grub by updating the menu.lst file in the /boot/grub folder of my existing Ubuntu installaion. This is the way I would like to go if possible?

---

### Post by volkswagner on 2008-05-21
> **roundhay said:**
> I have attached the output from sudo fdisk -l

It looks like I have 2 boot partitions, on is the XP partition and one is the Ubuntu partition.

I would rather not get into reinstallation of Grub, I've had loads of problems with this in the past. I'm fairly sure you can add the mythbuntu o/s to grub by updating the menu.lst file in the /boot/grub folder of my existing Ubuntu installaion. This is the way I would like to go if possible?

Sorry, I have no experience with multiple boot partitions.  Best to hear from the experts.

---

