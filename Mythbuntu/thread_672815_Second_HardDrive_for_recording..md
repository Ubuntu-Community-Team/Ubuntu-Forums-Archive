---
title: "Second HardDrive for recording."
date: 2008-01-20
forum: Mythbuntu
---

### Post by cutiger95 on 2008-01-20
How do I set-up my Mythbuntu system to use my secondary hard-drive.  The install is on the primary 125gig drive, but I would like for the recordings to occur on the secondary 250gig hard-drive.

How do I do this?

---

### Post by c0met on 2008-01-20
Is the secondary hard drive formatted? If not, the easiest way would probably be to boot from the Live CD and use the Partition Editor (System >> Administration) to set the drive as a single partition and then to format it. If you format it in FAT 32, keep in mind that 4 gigs is the maximum filesize that FAT 32 supports.

---

### Post by aaltieri on 2008-01-20
Greetings;

Here are two decent posts on adding hard drives to Ubuntu.  Warning:  They use only the command line.  Personally, I prefer that method myself.

[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/]("http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/")

[http://daryl.learnhouston.com/2006/05/03/adding-hard-drive-ubuntu-linux-box]("http://daryl.learnhouston.com/2006/05/03/adding-hard-drive-ubuntu-linux-box")

Both walk you through adding the device to /etc/fstab by using the /dev/hd* nomenclature.  If your fstab file refers to the partition by the UUID, I would add this new drive using the same formula.

To find the uuid of your new hard drive, type:

> 
sudo vol_id -u <partition>


On my machine, if I get:

> $ sudo vol_id -u /dev/sda1
7c4ec04a-919f-422f-80c3-fb558b9644b7

Then just add it to /etc/fstab the same as the other entry.

Do not user Fat 32.  If you have an HD tuner, an hour of TV can easily be a couple gigs.  Fat 32 is not very efficient at all.  Mine is xfs.  Not sure why...someone told me to use it.

just remember that to make the change in mythtv where the recordings are!  Again...I speak of some rather embarrassing  experience.


peace


--anthony

---

### Post by cutiger95 on 2008-01-22
Thanks guys.  This looks perfect.  I will try it out tomorrow night and report back.

---

### Post by ubnewbie2 on 2008-01-22
About choice of file system.  I have heard xfs is good.  ext3 is too slow when deleting large files.  fat32 is definitely not a good choice.

---

